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
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}