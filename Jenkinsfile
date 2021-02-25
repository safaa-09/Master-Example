pipeline {
   agent {
        docker { image 'node:14-alpine' }
    }
   
    stages {
        stage('checkount Git') {
            steps {
               git credentialsId: 'git_credentials', url: 'https://github.com/safaa-09/Master-Example.git'
            }
        }
        
         stage('Build Maven') {
            steps {
               sh 'mvn compile'
            }
        }
        
        stage('test Maven') {
            steps {
               sh 'mvn test'
            }
        }
        
                
        stage('package app Maven') {
            steps {
               sh 'mvn clean package'
            }
        }
        
        stage('Construction image Docker') {
            steps {
               sh 'docker build -t safaa09/miola1:v1 .'
            }
        }
        
         stage('Envoyer l\'image sur DockerHub') {
            steps {
              withCredentials([string(credentialsId: 'dockerhubpass', variable: 'dockermiolapass')]) {
              
                  sh 'docker login -u safaa09 -p ${dockermiolapass}'
              }
              sh 'docker push safaa09/miola1:v1'
             }
            }
        }
    
}
