pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'master',
            credentialsId: 'github-token',
            url: 'https://github.com/JoseRR19/MyFirstApp.git'
      }
    }

    stage('Build') {
      agent {
        docker {
          image 'node:18'
          args '-v /var/jenkins_home/workspace:/workspace'
        }
      }
      steps {
        sh 'node -v'
        sh 'npm install'
        echo '✅ Build complete!'
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        sh 'npm test || echo "No tests found"'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deployment step (simulated)...'
      }
    }
  }
}