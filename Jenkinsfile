pipeline {
  options {
    ansiColor('xterm')
  }   
  environment {
    registry           = "hub.docker.com/dksha17/java"
    registryCredential = 'docker-hub'
    dockerImage        = ''
  }
  agent any
  stages {
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build(registry , "-f Dockerfile .")
        }
      }
    }
    
    stage('push Image to acr') {
      steps{
        script {
          docker.withRegistry( 'https://' + registry, registryCredential ) {
          dockerImage.push()
          }
        }
      }
    }
  }
}
