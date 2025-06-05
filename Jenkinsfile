pipeline{
    agent any
    tools {
        maven "mvn"
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
                sh 'trivy fs .'
            }
        }
        stage('sonarqube') {
            steps{
                withSonarQubeEnv('sqube-server') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Chatapp \
                     -Dsonar.java.binaries=. \
                     -Dsonar.projectKey=Chatapp'''
                }
            }
        }
    }
}