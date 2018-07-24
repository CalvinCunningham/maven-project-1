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
                 mvn clean package
              }
              post {
              
                  success {
                      echo 'Now archiving ...'
                      archiveAftifacts artifacts: '**/*.war'
                  
                  }
                 
              
              }
        }
    
       stage ('Deploy') {
              steps {
              
                 echo "Echo Deploying"
              }
        }
    
    }
}