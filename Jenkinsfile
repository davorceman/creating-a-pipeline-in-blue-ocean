pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000 -e http_proxy=http://192.168.209.97:3128 -e https_proxy=http://192.168.209.97:3128'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
  }
}