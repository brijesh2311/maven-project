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
              
              
              stage('delpoy')
              {
                  steps {
                  
                      scp **/target/*.war ubuntu@184.72.108.1:/home/ubuntu/tomcat-staging/webapps
                  }
                  
               }


stage('delpoytoprod')
              {
                  steps {
                  timeout(2)
                  { 
                  input 'do you want to processed'
                  }
                      build 'tomcat-pro'
                  }
                  
               }
              
              
              
              
              
              
              
          }
    
     
}