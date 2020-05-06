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
        sh 'tidy -q -e *.html'
      }
    }

    stage('AWS', credentials: 'aws-static') {
      steps {
        s3DoesObjectExist(bucket: 'jenkinss3buck02', path: '/*', pathStyleAccessEnabled: true, payloadSigningEnabled: true)
      }
    }

  }
}
