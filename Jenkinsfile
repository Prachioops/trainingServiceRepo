pipeline{
       agent any
       options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
       }
       
       environment{
        DOCKERHUB_CREDENTIALS = credentials('prachi918-dockerhub')
       }
               stages {
               	stage('Build'){
                     steps{
                       sh 'docker build -t prachi918/gc:latest .'
                       
                     }
               }
               	stage('Login'){
                     steps{
                        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                     }
              }
               	stage('Push'){
                  steps{
                  sh 'docker push prachi918/gc:latest'
                  }
               }
               
               }
               	
               post{
               always {
                sh 'docker logout'
                
                 }
              }
          } 
               
  