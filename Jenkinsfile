pipeline {
agent any

```
stages {
    stage('Build') {
        steps {
            sh '''
                echo "Build Triggered Successfully"
                date
                hostname
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
```

Build Successful

Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Build URL: ${env.BUILD_URL}
"""
)
}

```
    failure {
        emailext(
            to: 'bhawanirajsinghranawat@gmail.com',
            subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: """
```

Build Failed

Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Build URL: ${env.BUILD_URL}
"""
)
}
}
}
