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
        sh 'docker build -t app2-mohammad:$BUILD_ID .'
      }
    }

    stage('Run & Test the Containers') {
      steps {
        sh 'docker run -d --name app2-mohammad -p 3000:8080 app2-mohammad:$BUILD_ID'
        sh 'sleep 5'
        sh 'docker stop app2-mohammad && docker rm app2-mohammad'
      }
    }

  }
}