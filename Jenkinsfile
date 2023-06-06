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
        sh 'sudo docker container run -d app6-mohammad'
      }
    }

  }
}