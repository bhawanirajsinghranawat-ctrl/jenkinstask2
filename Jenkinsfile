pipeline { agent any
stages {

    stage('Checkout') {
        steps {
            git branch: 'task2',
                url: 'https://github.com/bhawanirajsinghranawat-ctrl/jenkinstask2.git'
        }
    }

    stage('Build') {
        steps {
            sh '''
                echo "================================="
                echo "Build Triggered Successfully"
                echo "Date: $(date)"
                echo "Host: $(hostname)"
                echo "Current Branch:"
                git branch
                echo "================================="
                echo "Project Files:"
                ls -la
            '''
        }
    }
}

post {
    success {
        emailext(
            to: 'bhawanirajsinghranawat@gmail.com',
            subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: """
Build Successful
Job Name: ${env.JOB_NAME} Build Number: ${env.BUILD_NUMBER}
Build URL: ${env.BUILD_URL}
The GitHub commit triggered the Jenkins pipeline successfully. ““” ) }
    failure {
        emailext(
            to: 'bhawanirajsinghranawat@gmail.com',
            subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: """
Build Failed
Job Name: ${env.JOB_NAME} Build Number: ${env.BUILD_NUMBER}
Build URL: ${env.BUILD_URL}
Please check the Jenkins console output for details. ““” ) } } }
