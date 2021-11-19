pipeline {
    agent {
        node {
            label 'develop-test'
        }
    }
    triggers {
      GenericTrigger causeString: 'Github webhook build', genericVariables: [[defaultValue: 'main', key: 'BRANCH_NAME', regexpFilter: 'refs/heads/', value: '$.ref']], regexpFilterExpression: '', regexpFilterText: '', token: '', tokenCredentialId: ''
    }

    stages {
        stage('prepare-dir') {
            steps {
                dir(path: '/var/www/${BRANCH_NAME}')
            }
        }

        stage('checkout') {
            steps {
                git(url: 'https://github.com/gameAnalyticsGreg/test', branch: '${BRANCH_NAME}', credentialsId: 'git')
            }
        }
    }
}

// custom code:
// when { branch 'master' }
