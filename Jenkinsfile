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
        sh 'docker run --name app2-mohammad -d -p 3000:8080 app2-mohammad:$BUILD_ID'
        sh 'sleep 5'
        sh 'curl -v http://localhost:8080/app2-mohammad'
        sh 'docker stop app2-mohammad && docker rm app2-mohammad'
      }
    }

     stage('Upload to DockerHub') {
            
            steps {
         withCredentials(bindings: [usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'pass', usernameVariable: 'user')
                ]) {           
                sh "docker tag app1-mohammad:${env.BUILD_NUMBER} m7madm7mad/app1-mohammad:${env.BUILD_NUMBER}"
                sh "docker login -u $user -p $pass"
                sh "docker push m7madm7mad/app1-mohammad:${env.BUILD_NUMBER}"
                   }
            }
        }
    
  }
}
