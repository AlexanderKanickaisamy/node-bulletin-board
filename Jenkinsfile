pipeline {
environment {
  registry = "alexanderkanickaisamy/bulletinboard"
  registryCredential = 'dockerhub'
}
agent any
stages {
     stage('Building Image') {
     steps{
          script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
          }
       }
       }
       
       stage('Deploy Image') {
       steps{
            script {
            docker.withRegistry( '', 'dockerhub' ) {
                   dockerImage.push()
              }
              }
         }
         }
         
         stage('Remove Image') {
         steps{
              sh "docker rmi $registry:$BUILD_NUMBER"
         }
         }
     }
  }
  
  node {
    stage('Execute Image') {
            def customImage = docker.build("alexanderkanickaisamy/bulletinboard:${env.BUILD_NUMBER}")
            customImage.inside {
                 sh 'echo This is the code which is getting executed inside the container'
               }
            }
        }
   
