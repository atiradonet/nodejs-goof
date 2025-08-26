pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/atiradonet/nodejs-goof.git', branch: 'main'
      }
    }
    stage('Test') {
      steps {
        echo 'Snyk Security Testing'
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
        sh 'rm -rf /Projects/nodejs-goof && git clone https://github.com/atiradonet/nodejs-goof.git /Projects/nodejs-goof'
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
