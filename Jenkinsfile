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

    stage('Aqua Scanner') {
      steps {
        aquaMicroscanner(imageName: 'alpine:latest', onDisallowed: 'fail', notCompliesCmd: 'exit 1', outputFormat: 'json')
      }
    }

    stage('') {
      steps {
        s3Upload 'jenkinss3buck02'
      }
    }

  }
}