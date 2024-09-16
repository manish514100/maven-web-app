@Library("jenkins-shared-library@main") _   // Import the Shared Library

pipeline {
   agent {
       kubernetes {
           yaml getKanikoMavenYaml()                   // Retrieve agent YAML manifest
           defaultContainer getDefaultContainer() // Retrieve default container configuration
       }
   }

    stages{   
      stage('testing') {
        steps {
          container('maven') {
            sh "mvn clean package"
          }
        }  
      }
    stage('Build DockerImage with Kaniko') {
        environment {
        PATH = "/busybox:/kaniko:$PATH"
        }
        steps {
        container(name: 'kaniko', shell: '/busybox/sh') {


            sh '''#!/busybox/sh
            /kaniko/executor --context `pwd` --dockerfile Dockerfile --verbosity debug --destination=registry.tritec.in/myrepo/maven-webapp:v$BUILD_NUMBER
            '''
        }
        }
    }

    }
}