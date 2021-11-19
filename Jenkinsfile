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
                fileOperations([folderCreateOperation('/var/www/${env.BRANCH_NAME}')])
            }
        }

        stage('checkout') {
            steps {
                sh 'printenv'
                git(url: 'https://github.com/gameAnalyticsGreg/test', branch: '${env.BRANCH_NAME}', credentialsId: 'git')
            }
        }
    }
}

// custom code:
// when { branch 'master' }
