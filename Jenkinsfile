 pipeline {

  agent {
    docker { image 'node:8-alpine' }
  }
  stages {
    stage('Checkout'){
      steps {
        checkout scm
      }
    }

    stage ('Build') {
      steps {
        sh 'npm install'
      }
    }
  }
}

