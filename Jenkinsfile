pipeline {
    agent any
    stages {
      stage('Build') {
          steps {
              echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
              echo 'make'
              slackSend color: 'good', message: 'Message from Jenkins Pipeline'
          }
      }
      stage('Test'){
          steps {
              echo 'make check'
          }
      }
      stage('Deploy Test') {
          when {
             branch 'master'
             expression {
               currentBuild.result == null || currentBuild.result == 'SUCCESS'
             }
          }
          steps {
              echo 'make publish'
          }
      }
      stage('Deploy Staging') {
          when {
             branch 'prod'
             expression {
               currentBuild.result == null || currentBuild.result == 'SUCCESS'
             }
          }
          steps {
              echo 'make publish'
          }
      }
      stage('Sanity check') {
          when {
             branch 'prod'
          }
          steps {
             input "Does the staging environment for ${env.APP_NAME} look ok?"
          }
      }
      stage('Deploy Production') {
          when {
             branch 'prod'
             expression {
               currentBuild.result == null || currentBuild.result == 'SUCCESS'
             }
          }
          steps {
              echo 'make publish'
          }
      }
    }
}
