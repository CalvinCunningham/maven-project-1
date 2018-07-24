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
              
                 sh 'mvn clean package'
              }
              post {
              
                  success {
                      echo 'Now archiving ...'
                      archiveAftifacts artifacts: '**/targets/*.war'
                  
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