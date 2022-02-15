pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lrt
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
                  withAWS(region:'us-west-2',credentials:'aws-jenkins') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index1.html', bucket:'egs-devops-training')
                  }
              }
         }
     }
}
