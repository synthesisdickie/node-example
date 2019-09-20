pipeline {
  environment {
    registry = "synthesis/node-example"
  }
  agent any
  stages {
    stage('Building image') {
      steps{
        script {
          docker.build registry + "$latest"
        }
      }
    }
  }
}
