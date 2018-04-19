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
            timeout(time: 10, unit: 'SECONDS')
          }
          input {
            message 'Which Version?'
            id 'Deploy'
            parameters {
              choice(name: 'APP_VERSION', choices: '''v1.1
v1.2
v1.3''', description: 'What to deploy?')
            }
          }
          steps {
            echo "Deploying ${APP_VERSION}."
          }
          post {
            aborted {
              echo 'Why didn\'t you push my button?'
              
            }
            
          }
        }
        stage('Test scope') {
          agent any
          steps {
            echo 'APP_VERSION value!'
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