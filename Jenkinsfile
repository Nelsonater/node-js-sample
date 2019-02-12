 pipeline {

  agent any
  stages {
    stage('Checkout'){
      agent { label 'Node8'}
      steps {
        checkout scm
      }
    }

    stage ('Build') {
      agent { label 'Node8'}
      steps {
        sh 'npm install'
      }
    }
  }
}

