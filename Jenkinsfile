 pipeline {

  agent {
    docker {
      image 'node:8'
      args '--tmpfs /.config'
    }
  }
  stages {
    stage('Checkout'){
      steps {
        checkout scm
      }
    }

    stage ('Build') {
      steps {
        sh 'ls'
        sh 'mkdir /.npm'
        sh 'npm install --verbose'
      }
    }
  }
}

