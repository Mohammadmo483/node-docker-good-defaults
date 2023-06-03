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

    stage('build Docker Images') {
      steps {
        sh 'docker build -t app2-mohammad:$BUILD_ID .'
      }
    }

    stage('Run & Test the Containers') {
      steps {
        sh 'docker stop app2-mohammad && docker rm app2-mohammad'
        sh 'docker run --name app2-mohammad -d -p 3000:3000 app2-mohammad:$BUILD_ID'
        sh 'sleep 5'
        sh 'curl -v http://localhost:3000/app2-mohammad'
      }
    }

  }
}
