pipeline {
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/Mohammadmo483/node-docker-good-defaults.git', changelog: true, poll: true, branch: 'main')
      }
    }

    stage('Build Docker Images') {
      steps {
        sh 'docker build -t app6-mohammad:$BUILD_ID .'
      }
    }

    stage('Run & Test the Containers') {
      steps {
        sh '''docker run  --name app6-mohammad -dp 3000:8080  app6-mohammad:$BUILD_ID
'''
      }
    }

  }
}