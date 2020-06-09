pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }
         stage('Lint HTML') {
              steps {
                  sh 'echo "Tidy Element is Being Tested!!"'
              }
         }  
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-1',credentials:'MyAwsCred') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'shubham-static-jenkins-pipeline')
                  }
              }
         }
     }
}
