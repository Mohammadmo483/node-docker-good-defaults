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
        sh 'docker build -t app3-mohammad:$BUILD_ID .'
      }
    }

    stage('Run & Test the Containers') {
      steps {
        sh 'docker stop app3-mohammad && docker rm app3-mohammad'
        sh 'docker run -d --name app3-mohammad -p 80:8080 app3-mohammad:$BUILD_ID'
        sh 'sleep 5'
      }
    }

  }
}