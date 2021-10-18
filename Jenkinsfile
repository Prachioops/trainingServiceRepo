pipeline{
       agent any
       options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
       }
       
       environment{
        DOCKERHUB_CREDENTIALS_USR = 'prachi918-dockerhub'
        DOCKERHUB_CREDENTIALS_PSW = 'f71a3a0e-a62a-4722-9049-8ea3d604ab3f'
       }
       stages {
         stage('Build'){
           steps{
             bat 'docker build -t prachi918/gc:latest .'
                       
                 }
               }
          stage('Login'){
           steps{
              bat 'echo "$DOCKERHUB_CREDENTIALS_PSW" | docker login --username "$DOCKERHUB_CREDENTIALS_USR" --password-stdin'
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
               
  