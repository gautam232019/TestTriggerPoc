pipeline {
    agent any

    stages {
        stage('Trigger') {
            steps {
                 script {
                    def changedDirectory = sh(script: 'git diff --name-only HEAD^ HEAD', returnStdout: true).trim()
                    print(changedDirectory)

                    def webhookPayload = readFile("${env.GITHUB_EVENT_PATH}")

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