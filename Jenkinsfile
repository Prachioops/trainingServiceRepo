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
              bat 'docker login -u prachi918-dockerhub'
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
               
  