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