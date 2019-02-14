 pipeline {

  agent {
    docker {
      image 'node:8'
      args '-u root:root'
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
        sh 'pwd'
        sh 'npm install --verbose'
        sh 'ls'
      }
    }
  }
}

