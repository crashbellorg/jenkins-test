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
            input 'Do you approve deployment?'
            steps {
                sh 'make publish'
            }
        }
    }
}
