pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                    echo "Build Triggered Successfully"
                    date
                    hostname
                    ls -la
            
            }
        }
    }

    post {
        success {
            emailext(
                to: '${DEFAULT_RECIPIENTS}',
                subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
Build Successful

Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Build URL: ${env.BUILD_URL}
"""
            )
        }

        failure {
            emailext(
                to: '${DEFAULT_RECIPIENTS}',
                subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
Build Failed

Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Build URL: ${env.BUILD_URL}
"""
            )
        }
    }
}
