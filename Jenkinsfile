pipeline {
    agent {
        node {
            label 'develop-test'
        }
    }

    stages {
        stage('prepare-dir') {
            steps {
                sh 'printenv'
                sh '''mkdir -p /var/www/$BRANCH_NAME'''
            }
        }

        stage('checkout') {
            steps {
                sh 'printenv'
                git(url: 'https://github.com/gameAnalyticsGreg/test', branch: '$BRANCH_NAME', credentialsId: 'git')
            }
        }
    }
}

// custom code:
// when { branch 'master' }
