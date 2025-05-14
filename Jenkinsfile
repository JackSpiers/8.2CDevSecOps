pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/JackSpiers/8.2CDevSecOps.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        // Unix: sh; Windows: bat
        sh 'npm install'
      }
    }

    stage('Run Tests') {
      steps {
        // allow failures so pipeline continues
        sh 'npm test || true'
      }
    }

    stage('Generate Coverage Report') {
      steps {
        sh 'npm run coverage || true'
      }
    }

    stage('NPM Audit (Security Scan)') {
      steps {
        sh 'npm audit || true'
      }
    }
  }
}
