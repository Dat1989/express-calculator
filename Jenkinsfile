pipeline {
  agent any
  stages {
    stage('Install') {
      steps {
        npm install
      }
    }
    stage('Test') {
      steps {
        npm run unit-test
      }
      steps {
        npm run integration-test
      }
    }
  }
}
    
