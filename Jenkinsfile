pipeline {
  agent {
    node {
      label 'develop-test'
    }

  }
  stages {
    stage('prepare-dir') {
      steps {
        dir(path: '/var/www/${BRANCH}')
      }
    }

    stage('checkout') {
      steps {
        git(url: 'https://github.com/gameAnalyticsGreg/test', branch: '${BRANCH}', credentialsId: 'git')
      }
    }

  }
}