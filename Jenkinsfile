pipeline {
    agent {
        node {
            label 'develop-test'
            customWorkspace "/var/www/${BRANCH_NAME}"
        }
    }

    stages {
        stage('Prepare directories') {
            steps {
                // do chmods etc
                sh 'printenv'
            }
        }

        stage('Prepare assets'){
            when { changeset "**/*.js" }
            steps {
                sh 'printenv'
            }
        }

        stage('Run tests') {
            when { not { branch 'master'} }
            steps {
                sh 'printenv'
            }
        }
    }
}
