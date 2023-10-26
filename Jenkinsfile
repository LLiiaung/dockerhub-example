pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('darinpope-dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        bat 'docker build -t lwsdnh/dp-alpine:latest .'
      }
    }
    stage('Login') {
      steps {
        bat 'echo dckr_pat_39wfm7AtuW7edX1eFBOe-_4FTwg | docker login -u lwsdnh -p '
        
      }
    }
    stage('Push') {
      steps {
        bat 'docker push lwsdnh/dp-alpine:latest'
      }
    }
  }
  post {
    always {
      bat 'docker logout'
    }
  }
}
