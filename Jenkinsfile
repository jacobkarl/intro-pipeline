pipeline {
  agent none
  stages {
    stage('Say Hello') {
      parallel {
        stage('Say name variable') {
          agent any
          steps {
            echo "Hello ${params.Name}!"
            echo "Hello ${MY_NAME}!"
          }
        }
        stage('Deploy') {
          options {
            timeout(time: 20, unit: 'SECONDS')
          }
          input {
            message 'Should we continue?'
          }
          steps {
            echo 'Continuing with deployment'
          }
        }
      }
    }
  }
  environment {
    MY_NAME = 'Mary'
  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
}