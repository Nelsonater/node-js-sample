 pipeline {

  agent {
    docker {
      image 'node:8'
      args '-u 0:0'
      reuseNode true
    }
  }
  environment {
    ARTIFACTORY_URL = credentials('artifactoryURL')
  }
  stages {
    stage('Checkout'){
      steps {
        checkout scm
      }
    }
    stage ('Build') {
      steps {
        sh 'npm install --verbose'
      }
    }
    stage ('Deploy') {
      steps {
        withCredentials([usernamePassword(credentialsId: "artifactoryCreds", passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')]) {
          sh "curl -k -u $USERNAME:$PASSWORD ${env.ARTIFACTORY_URL}/artifactory/api/npm/auth > .npmrc"               
        }
        sh "echo 'registry=${env.ARTIFACTORY_URL}/artifactory/api/npm/alex-npm' >> .npmrc"
        sh 'echo "email=alexn@fake.email" >> .npmrc'
        sh 'echo "strict-ssl=false" >> .npmrc'
        sh 'npm publish'
      }
    }
    stage ('Static Code Analysis') {
      def scannerHome = tool 'sonarScanner';
      withSonarQubeEnv('SonarQube Server') {
        sh "${scannerHome}/bin/sonar-scanner"
      }
    }
  }
}

