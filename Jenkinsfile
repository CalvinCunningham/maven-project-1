pipeline {
    agent any
    stages {
    
        stage ('Init') {
              steps {
              
                 echo "Echo Testing"
              }
        }
        
        stage ('Build') {
              steps {
                 echo 'Now cleaning package'
                 bat 'mvn clean package'
              }
              post {
              
                  success {
                      echo 'Now archiving ...'
                      archiveArtifacts artifacts: '**/*.war'
                  
                  }
                 
              
              }
        }
    
       stage ('Deploy') {
              steps {
              
                 echo "Echo Deploying to staging"
                 build job: 'Depoy-to-Staging'
              }
        }
        
        stage ('Deploy to Production') {
              steps {
                  timeout(time:5, unit:'DAYS'){
                      Input Message: 'Approve Production Deployment?'
                  }
                  
                  
                 echo "Echo Deploying to production"
                 build job: 'deploy-to-prod'
              }
              post {
                  success {
                      echo 'Code Deployed to Production'
                  }
                  failure {
                     echo 'Deployment Failed'
                  }
              
              }
        }
    
    }
}