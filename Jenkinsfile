pipeline {
    agent any
    stages {
     
        stage('CD') {
            steps {
                script {
                      sh 'kubectl apply -Rf ./app'
                }
            }
        }
    }
    post {
          success {
              slackSend (message:"Deploy successfully - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)")
          }
          failure {
              slackSend (message:"Deploy failed  - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)")
          }
      }
}
