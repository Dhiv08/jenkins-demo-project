pipeline {
  agent any

  parameters { ... }

  stages {
    stage('Checkout') { ... }
    stage('Build') { ... }
    stage('Run') { ... }
    stage('Code Scan (optional)') { ... }

    stage('Check Secret Text') {
      steps {
        withCredentials([string(credentialsId: 'git-token', variable: 'GIT_TOKEN')]) {
          script {
            if (isUnix()) sh 'echo "Secret text loaded: YES"'
            else          bat 'echo Secret text loaded: YES'
          }
        }
      }
    }
  }
}
