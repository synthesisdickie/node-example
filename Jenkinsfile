pipeline {
  environment {
    registry = "synthesis/node-example"
  }
  agent any
  stages {
    stage('Building image') {
      steps{
        script {
          // docker.build registry + ":latest"
          //sh "docker -v jenkins-data:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock build -t synthesis/node-example:latest ."
          sh "docker build -t synthesis/node-example:latest ."
        }
      }
    }
    stage('Push image') {
      steps{
        script {
          // docker.build registry + ":latest"
          sh "docker push synthesis/node-example:latest"
        }
      }
    }
  }
}
