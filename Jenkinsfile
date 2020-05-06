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

    stage('aws') {
      steps {
        s3Upload(bucket: 'jenkinss3buck02', pathStyleAccessEnabled: true, payloadSigningEnabled: true, acl: 'Private', path: '/', text: 'hello')
      }
    }

  }
}