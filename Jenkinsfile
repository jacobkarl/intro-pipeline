pipeline {
  agent none
  libraries {
    lib("SharedLibs")
  }
  stages {
    stage('Get Kernel') {
      agent any
      steps {
        script {
          try {
            KERNEL_VERSION = sh (script: "uname -r", returnStdout: true)
          } catch(err) {
            echo "CAUGHT ERROR: ${err}"
            throw err
          }
        }
        
      }
    }
    stage('Say Kernel') {
      agent any
      steps {
        echo "${KERNEL_VERSION}"
      }
    }
    stage('Shared Lib') {
         steps {
             helloWorld("Jenkins")
         }
      }
  }
  environment {
    MY_NAME = 'Mary'
  }
  post {
    aborted {
      echo 'Why didn\'t you push my button?'
      
    }
    
  }
}
