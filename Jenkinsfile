pipeline {
    agent any

    stages {
        stage('Trigger') {
            steps {
                 script {
                    def changedDirectory = sh(script: 'git diff --name-only HEAD^ HEAD', returnStdout: true).trim()
                    print(changedDirectory)

                    def webhookPayload = currentBuild.rawBuild.getAction(hudson.plugins.git.util.DefaultBuildChooser$Context).getEvent()
                    echo "GitHub Webhook Payload:"
                    echo "${webhookPayload}"
                    
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