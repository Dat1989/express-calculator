pipeline {
  agent any
  stages {
    stage('Install') {
      steps {
        npm install
      }
    }
    stage('Unit test') {
      steps {
        npm run unit-test
      }
    }
    stage('Integration-test') {
      steps {
        npm run integration-test
      }
    }
  }
}
    
