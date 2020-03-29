clearpipeline {
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
        sh 'tidy -q -e *.html'
      }
    }
    
    stage('Upload to AWS') {
      steps {
        withAWS(region: 'us-east-1', credentials: 'MyAwsCred') {
          sh 'echo "Uploading content with AWS credentials"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html', bucket: 'shubham-static-jenkins-pipeline')
        }

      }
    }

  }
}
