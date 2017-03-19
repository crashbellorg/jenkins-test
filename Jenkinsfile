pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'make'
                slackSend color: 'good', message: 'Message from Jenkins Pipeline'
            }
        }
        stage('Test'){
            steps {
                echo 'make check'
            }
        }
        stage('Deploy') {
            steps {
                echo 'make publish'
            }
        }
    }
}
