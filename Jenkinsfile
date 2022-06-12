pipeline {
  agent any
  stages {
    stage('Install') {
      steps {
        echo 'Installing...'
        sh 'npm install'
      }
    }
    stage('Unit test') {
      steps {
        echo 'Running unit test...'
        sh 'npm run unit-test'
      }
    }
    stage('Integration-test') {
      when {
        anyOf {
          branch 'main'
          branch 'develop'
        }
      }
      steps {
        echo 'Running integration test...'
        sh 'npm run integration-test'
      }
    }
    stage('Delivery') {
      when {
        branch 'main'
      }
      steps {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
          def image = docker.build("Dat1989/express-calculator")
          image.push()
        }
      }  
    }
  }
} 
