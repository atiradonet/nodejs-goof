pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/atiradonet/nodejs-goof.git', branch: 'main'
      }
    }
    stage('Test: Snyk Security Testing') {
      steps {
        snykSecurity(
          snykInstallation: 'snyk-app',
          snykTokenId: 'snyk-token',
          failOnIssues: false,
          severity: 'high'
        )
      }
    }
    stage('Deploy and Run with Docker Compose') {
      steps {
        sh 'rm -rf /Projects/nodejs-goof'
        dir('/Projects') {
          sh 'git clone https://github.com/atiradonet/nodejs-goof.git'
        }
        dir('/Projects/nodejs-goof') {
          sh 'docker-compose down'
          sh 'docker-compose pull'
          sh 'docker-compose up --build -d'
          sh 'docker image prune -f'
        }
      }
    }
  }
}
