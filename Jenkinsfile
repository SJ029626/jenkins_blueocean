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

    stage('') {
      steps {
        s3FindFiles(bucket: 'jenkins2602', pathStyleAccessEnabled: true, payloadSigningEnabled: true)
      }
    }

  }
}