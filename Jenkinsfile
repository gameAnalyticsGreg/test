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
                checkout(
                    [
                        $class: 'GitSCM',
                            branches: [[name: '$BRANCH_NAME']],
                            extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: '/var/www/$BRANCH_NAME']],
                            userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/gameAnalyticsGreg/test']]
                    ]
                )
            }
        }
    }
}

// custom code:
// when { branch 'master' }
