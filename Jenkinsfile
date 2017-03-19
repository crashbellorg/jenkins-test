pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'make'
                slackSend color: 'good', message: 'Message from Jenkins Pipeline'
            }
        }
        stage('Test'){
            steps {
                sh 'make check'
            }
        }
        stage('Deploy') {
            steps {
                input 'Do you approve deployment?'
                sh 'make publish'
            }
        }
    }
}
