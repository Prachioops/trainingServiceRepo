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
             bat 'docker build -t prachi918/gc:latest .'
                       
                 }
               }
          stage('Login'){
           steps{
              bat 'echo "" | docker login --username prachi918-dockerhub --password-stdin'
                 }
              }
          stage('Push'){
           steps{
              bat 'docker push prachi918/gc:latest'
                  }
               }
               
            }
               	
           post{
            always {
              bat 'docker logout'
                
             }
           }
         } 
               
  