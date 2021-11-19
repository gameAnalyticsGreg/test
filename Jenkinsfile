pipeline {
    agent {
        node {
            label 'develop-test'
            customWorkspace "/var/www/${BRANCH_NAME}"
        }
    }

    options {
        // Keep the 10 most recent builds
        buildDiscarder(logRotator(numToKeepStr:'50'))
    }

    stages {
        stage('Prepare directories') {
            steps {
                // do chmods etc
                // current working dir is /var/www/${BRANCH_NAME}
                sh 'printenv'
            }
        }

        stage('Prepare assets'){
            when {
                // run this step ONLY if changes contain css and js files
                anyOf {
                    changeset "**/*.js";
                    changeset "**/*.css";
                }
            }
            steps {
                // current working dir is /var/www/${BRANCH_NAME}
                sh 'printenv'
            }
        }

        stage('Run tests') {
            // uncomment this to exclude this step for that branch
            // when { not { branch 'master'} }
            steps {
                // current working dir is /var/www/${BRANCH_NAME}
                sh 'printenv'
            }
            post {
                success {
                    publishHTML([
                        allowMissing: false,
                        alwaysLinkToLastBuild: false,
                        keepAll: false,
                        reportDir: 'tests/_output/',
                        reportFiles: 'records.html',
                        reportName: 'Report',
                        reportTitles: ''
                    ])
                }
            }
        }
    }

    post {
        failure {
            echo 'Hello World'
        }
    }
}
