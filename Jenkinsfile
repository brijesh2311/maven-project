pipeline {
    
        agent any
        tools {
        	maven 'maven3'
        	jdk 'java8'
        }
          stages {
              
              stage('init'){
                  steps {
                      echo "this is initlizages"
                  }
              }
              
              stage('Build'){
                  steps {
                      sh 'mvn clean package checkstyle:checkstyle'
                  }
                          post {
                              success
                              {
                              echo "rub cheksytle"
                              checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
                              echo " unit test"
                              junit '**/surefire-reports/*.xml'
                              echo " arvihe afifctate"
                              archiveArtifacts '**/*.war'

                              }

                          }
                  






              }
              
              
              stage('delpoy'){
                  steps {
                      echo "this is deploy"
                  }
              }
              
              
              
              
              
              
          }
    
     
}