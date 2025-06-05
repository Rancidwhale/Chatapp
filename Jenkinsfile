pipeline{
    agent any
    tools {
        maven "mvn"
    }
    environment {
        SCANNER_HOME=tool 'sqube-scanner'
        TOMCAT_PATH = '/usr/local/tomcat/webapps'
    }
    stages {
        stage('git scm') {
            steps {
                git branch: 'dev', url: 'https://github.com/Rancidwhale/Chatapp.git'
            }
        }
        stage('validate') {
            steps{
                sh 'mvn validate'
            }
        }
        stage('compile') {
            steps{
                sh 'mvn compile'
            }
        }
        stage('trivy scan') {
            steps{
                sh 'trivy fs --severity LOW,MEDIUM,HIGH,CRITICAL -o file-scan.html .'
            }
        }
        stage ('Dependency Checks'){
            parallel{
                stage('sonarqube') {
                    steps{
                        withSonarQubeEnv('sqube-server') {
                            sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Chatapp \
                             -Dsonar.java.binaries=. \
                             -Dsonar.projectKey=Chatapp'''
                        }
                    }
                }
                stage('OWASP FS SCAN') {
                    steps {
                        withCredentials([string(credentialsId: 'nvd-api-key', variable: 'NVD_API_KEY')]) {
                            dependencyCheck additionalArguments: "--scan ./ --disableYarnAudit --disableNodeAudit --nvdApiKey ${NVD_API_KEY}", odcInstallation: 'owasp'
                        }
                        dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
                    }
                }
            }
        }
        stage('Build'){
        steps{
            sh 'mvn package -DskipTest'
            }
        }
        stage('run app'){
            steps{
                sh 'mv target/*.war $TOMCAT_PATH/ROOT.war'
            }
        }
        
    }
}