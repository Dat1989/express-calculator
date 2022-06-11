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
  }
} 
