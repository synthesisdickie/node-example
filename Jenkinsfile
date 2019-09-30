pipeline {
  environment {
    registry = "synthesis/node-example"
    registryCredential = 'dockerhub'
    dockerImage = ''
    dockerImageLatest = ''
  }
  agent any
  stages {
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":v" + "$BUILD_NUMBER"
          dockerImageLatest = docker.build registry + ":latest"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
            dockerImageLatest.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:v$BUILD_NUMBER"
        sh "docker rmi $registry:latest"
      }
    }
  }
}
