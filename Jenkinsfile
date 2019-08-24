pipeline {
  agent any
  environment {
    USER = "build"
  }
  parameters{
    string(name: 'project_name',description: 'Enter Your Project name - We capture it for tracking and reporting purpose')
    string(name: 'release_name',description: 'Enter Your Release name/number')
  }
  stages {
    stage('check environment variables') {
      steps{
        echo "hello world"
        echo "$USER"
      }
    }
  }
}
