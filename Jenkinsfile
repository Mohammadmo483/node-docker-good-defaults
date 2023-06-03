pipeline {
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/Mohammadmo483/node-docker-good-defaults.git', branch: 'main', changelog: true, poll: true)
      }
    }

  }
}