pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }

    stage('Build') {
      steps { sh 'javac app.java' }
    }

    stage('Run') {
      steps { sh 'java app' }
    }
  }
}
