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
    }
}