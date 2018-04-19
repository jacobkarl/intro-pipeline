pipeline {
  agent none
  stages {
    stage('Say Hello') {
      parallel {
        stage('Say name variable') {
          agent any
          steps {
            echo "Hello ${MY_NAME}!"
          }
        }
      }
    }
  }
  environment {
    MY_NAME = 'Mary'
  }
}