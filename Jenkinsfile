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
    stage('Delivery-Redovisning') {
      when {
        branch 'main'
      }
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            def image = docker.build("dat1989/express-calculator")
            image.push("$BUILD_ID")
          }
        }
      }  
    }
  }
} 
