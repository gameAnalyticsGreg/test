pipeline {
    properties([pipelineTriggers([githubPush()])])

    agent {
        node {
            label 'develop-test'
        }
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
