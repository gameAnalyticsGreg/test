pipeline {
    agent {
        node {
            label 'develop-test'
        }
    }

    triggers {
        GenericTrigger(
            causeString: 'Github webhook build',
            genericVariables: [
                [defaultValue: 'main', key: 'BRANCH_NAME', regexpFilter: 'refs/heads/', value: '$.ref']

            ],
            regexpFilterExpression: '',
            regexpFilterText: '',
            token: '',
            tokenCredentialId: ''
        )
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
