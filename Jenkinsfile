pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        script {
          if (isUnix()) {
            sh 'javac app.java'
          } else {
            bat 'javac app.java'
          }
        }
      }
    }

    stage('Run') {
      steps {
        script {
          if (isUnix()) {
            sh 'java app'
          } else {
            bat 'java app'
          }
        }
      }
    }
  }
}
