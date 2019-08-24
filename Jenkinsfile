pipeline {
  agent any
  environment {
    USER = "build"
  }
  parameters{
    string(name: 'project_name',description: 'Enter Your Project name - We capture it for tracking and reporting purpose')
    string(name: 'release_name',description: 'Enter Your Release name/number')
    choice(name: 'variant', choices: "IOS\nWebApp/DistributionSystems+Desktop\nAndroid\nMainframe", description: 'Select Variant for VPAT')
    string(name: 'start_date',defaultValue: 'dd/mm/yyyy', description: 'Tentative VPAT Start Date in dd/mm/yyyy format')
    string(name: 'finish_date',defaultValue: 'dd/mm/yyyy', description: 'Tentative VPAT End Date in dd/mm/yyyy format')
    string(name: 'release_date',defaultValue: 'dd/mm/yyyy', description: 'Tentative your product release Date in dd/mm/yyyy format')
            
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
