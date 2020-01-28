pipeline {
  options {
    ansiColor('xterm')
  }   
  environment {
    registry           = "deeksha17/java"
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
          docker.withRegistry( '', registryCredential ) {
          dockerImage.push()
          }
        }
      }
    }
  }
}
