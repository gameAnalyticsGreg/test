pipeline {
    agent {
        node {
            label 'jenkins-test'
            customWorkspace "/var/www/${BRANCH_NAME}"
        }
    }

    stages {
        stage('prepare-dir') {
            steps {
                sh 'printenv'
            }
        }

        stage('checkout') {
            steps {
                sh 'printenv'
            }
        }
    }
}

// custom code:
// when { branch 'master' }
