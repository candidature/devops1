pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
    disableConcurrentBuilds()
    timeout(time: 180, unit: 'DAYS')
  }
  environment {
    USER = "build"
    ADMIN_EMAIL = 'pankaj.gupta@broadcom.com'
    
  }
  parameters{
    choice(name: 'dry_run', choices: "yes\nno", description: 'Dry run')
    string(name: 'project_name',description: 'Enter Your Project name - We capture it for tracking and reporting purpose')
    string(name: 'email',description: 'email id to whom VPAT document has to be sent')
    string(name: 'release_name',description: 'Enter Your Release name/number')
    choice(name: 'variant', choices: "IOS\nWebApp/DistributionSystems+Desktop\nAndroid\nMainframe", description: 'Select Variant for VPAT')
    string(name: 'start_date',defaultValue: 'dd/mm/yyyy', description: 'Tentative VPAT Start Date in dd/mm/yyyy format')
    string(name: 'finish_date',defaultValue: 'dd/mm/yyyy', description: 'Tentative VPAT End Date in dd/mm/yyyy format')
    string(name: 'release_date',defaultValue: 'dd/mm/yyyy', description: 'Tentative your product release Date in dd/mm/yyyy format')
            
  }
  stages {
  
    stage('check environment') {
      steps{
        script {
          if("${params.dry_run}" == 'yes') {
            currentBuild.result = 'ABORTED'
            error('Current Build aborted, job parameterized')
          }
          echo "hello world"
          echo "$USER"
        }
        }
    }
    
    stage('Sending documents in email') {
      steps{
        script {
        echo "Sending documents by email to ..."
        echo "$ADMIN_EMAIL"
        
        echo "${params.email}"
        emailext(mimeType: 'text/html', replyTo: 'xxxx', attachmentsPattern: '**/Jenkinsfile', body: 'Find attachments', subject: 'test', to: 'pankaj.gupta@broadcom.com')
        }
      }
    }
    
    stage('Sending email for support team') {
      steps{
        script {
        echo "Sending documents by email to ..."
        echo "$ADMIN_EMAIL"
        }
      }
    }
    stage('Request for approval') {
      steps{
        script {
        timeout(time:10, unit:'DAYS') {
          userInput = input(
                    id: 'Approve1', 
                    message: 'Do NOT click unless you already login! Only authorized person shall approve', 
                    submitterParameter: 'approver' , 
                    parameters: [
                      [$class: 'BooleanParameterDefinition', 
                       defaultValue: true, description: '', name: 'Please confirm you approve this release']])
          
        }//timeout end
        }//script end
      }//step end
      }//stage end
      
    }//stages end
}
