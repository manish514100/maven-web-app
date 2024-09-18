@Library("jenkins-shared-library@main") _   // Import the Shared Library

pipeline {
   agent {
       kubernetes {
           yaml getKanikoMavenYaml()                   // Retrieve agent YAML manifest
           defaultContainer getDefaultContainer() // Retrieve default container configuration
       }
   }

    stages{   
      stage('Maven Build') {
        steps {
          container('maven') {
            sh "mvn clean package"
          }
        }  
      }
    stage('Build DockerImage with Kaniko') {
         buildkaniko(env: 'maven')
      
    }

    }
}