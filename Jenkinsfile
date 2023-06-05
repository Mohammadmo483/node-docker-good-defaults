pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git 'https://github.com/lidorg-dev/node-docker-good-defaults.git'
      }
    }

    stage('Build Docker Images') {
      steps {
        script {
          def dockerImage = docker.build('your-image-name:tag', '-f path/to/Dockerfile .')
        }

      }
    }

    stage('Run & Test the Containers') {
      steps {
        script {
          docker.withServer('tcp://docker-host:2376') {
            def composeCommand = "docker-compose -f path/to/docker-compose.yml up -d"
            sh composeCommand

            // Run your tests against the containers
            // ...
          }
        }

      }
    }

    stage('Upload to DockerHub') {
      steps {
        script {
          def dockerImage = docker.build('your-image-name:tag', '-f path/to/Dockerfile .')
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-credentials-id') {
            dockerImage.push()
          }
        }

      }
    }

  }
}