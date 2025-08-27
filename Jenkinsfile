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
          failOnIssues: true,
          severity: 'low'
        )
      }
    }
    stage('Deploy and Run with Docker Compose') {
      steps {
        sh 'docker-compose down'
        sh 'docker system prune -a'
        sh 'rm -rf ~/projects/nodejs-goof'
        dir('~/projects') {
          sh 'git clone https://github.com/atiradonet/nodejs-goof.git'
        }
        dir('~/projects/nodejs-goof') {
          sh 'docker-compose pull'
          sh 'docker-compose up --build -d'
          sh 'docker image prune -f'
        }
      }
    }
  }
}
