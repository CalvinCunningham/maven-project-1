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
    
    }
}