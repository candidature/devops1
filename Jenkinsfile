pipeline {
  agent any
  environment {
    USER = 'build'
  }
  stages {
    stage('check environment variables') {
      steps{
        echo "hello world"
        echo $USER
      }
    }
  }
}
