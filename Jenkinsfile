pipeline {
  agent none
  stages {
    stage('Say Hello') {
      parallel {
        stage('Say name variable') {
          agent any
          steps {
            echo "Hello ${MY_NAME}!"
            echo "${TEST_USER_USR}"
            echo "${TEST_USER_PSW}"
          }
        }
      }
    }
  }
  environment {
    MY_NAME = 'Mary'
    TEST_USER = credentials('test-user')
  }
}