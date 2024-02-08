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
    stage('Upload to AWS') {
      steps {
        withAWS(region: 'us-east-1', credentials: 'Jenkins-cred') {
          sh 'echo "Uploading content with AWS creds"'
          s3Upload(profileName:"test" entries{bucket:'clcm3506-ash-group' sourceFile:'*'})
        }
      }
    }
  }
}
