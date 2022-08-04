pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh '''ls
echo "File listed above"
pwd'''
          }
        }

        stage('') {
          steps {
            sh 'sudo apt install git'
          }
        }

      }
    }

    stage('Mail Sending') {
      steps {
        mail(subject: 'All is OK', body: 'Trying to Send it', bcc: 'aman.pathak@aitglobalinc.com', cc: 'aman07pathak@gmail.com', from: 'aman.pathak@aitglobalinc.com')
      }
    }

  }
}