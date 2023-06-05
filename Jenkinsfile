pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Clone the repository
                git 'https://github.com/lidorg-dev/node-docker-good-defaults.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                // Build the Docker images
                script {
                    def dockerImage = docker.build('your-image-name:tag', '-f path/to/Dockerfile .')
                }
            }
        }

        stage('Run & Test the Containers') {
            steps {
                // Run and test the containers
                script {
                    // Use Docker Compose to run the containers
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
                // Push the built Docker images to DockerHub
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
