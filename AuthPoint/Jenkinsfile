pipeline {
    agent any

    stages {
        stage('Trigger') {
            steps {
                 script {
                    def changedDirectory = sh(script: 'git diff --name-only HEAD^ HEAD', returnStatus: true).trim()

                    if (changedDirectory.contains('AuthPoint')) {
                        build(job: 'Authpoint', wait: false)
                    }

                    if (changedDirectory.contains('Panda')) {
                        build(job: 'Panda', wait: false)
                    }
                }
            }
        }
    }
}