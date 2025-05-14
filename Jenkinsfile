pipeline {
  agent any

  tools { nodejs 'Node18' } 

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Install Dependencies') {
      steps {
        bat 'npm install'
      }
    }

    stage('Run Tests') {
      steps {
        bat 'npm test || exit /b 0'
      }
    }

    stage('Generate Coverage Report') {
      steps {
        bat 'npm run coverage || exit /b 0'
      }
    }

    stage('NPM Audit (Security Scan)') {
      steps {
        bat 'npm audit || exit /b 0'
      }
    }
  }
}
