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
        sh 'docker run --name app2-mohammad -d -p 80:80 app2-mohammad:$BUILD_ID'
        sh 'sleep 5'
        sh 'curl localhost:8080'
        sh 'docker stop app2-mohammad && docker rm app2-mohammad'
      }
    }

    stage('Upload to DockerHub') {
      steps {
        withCredentials(bindings: [usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'pass', usernameVariable: 'user')
                                                                ]) {
          sh "docker tag app2-mohammad:$BUILD_ID m7madm7mad/app2-mohammad:$BUILD_ID"
          sh "docker login -u $user -p $pass"
          sh "docker push m7madm7mad/app2-mohammad:$BUILD_ID"
        }

      }
    }

  }
}