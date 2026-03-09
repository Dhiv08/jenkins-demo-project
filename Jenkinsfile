pipeline {
  agent any

  parameters {
    string(name: 'BRANCH', defaultValue: 'main', description: 'Git branch to build')
    booleanParam(name: 'RUN_SCAN', defaultValue: false, description: 'Run optional code scan stage')
  }

  stages {
    stage('Checkout') {
      steps {
        // Checkout the branch chosen in the parameter
        git branch: params.BRANCH,
            url: 'https://github.com/Dhiv08/jenkins-demo-project.git',
            credentialsId: 'git-userpass'   // change if your Jenkins credential ID is different
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

    stage('Code Scan (optional)') {
      when {
        expression { return params.RUN_SCAN == true }
      }
      steps {
        script {
          if (isUnix()) {
            sh 'echo Running code scan...'
          } else {
            bat 'echo Running code scan...'
          }
        }
      }
    }
  }
}

stage('Check Secret Text') {
  steps {
    withCredentials([string(credentialsId: 'git-token', variable: 'GIT_TOKEN')]) {
      script {
        if (isUnix()) {
          sh 'echo "Secret text loaded: YES"'
        } else {
          bat 'echo Secret text loaded: YES'
        }
      }
    }
  }
}
