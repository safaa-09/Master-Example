pipeline {
    agent any

    tools {
        //Install the Maven version configured as "M3" and add it to the path.
        maven "apache-maven-3.6.0"
}

 stages{
     stage("Check GitHub"){
         steps{
         git credentialsId: 'git_credentials', url: 'https://github.com/safaa-09/Triang07.git'
         }
     }
     
     stage("Build Code"){
         steps{
             sh ' mvn compile'
             
         }
     }
     
      stage("Test Unitaire"){
         steps{
             sh 'mvn test'
             
         }
     }
     
          stage("Packaging de l'application "){
         steps{
             sh 'mvn package'
             
         }
          }
 }


}
