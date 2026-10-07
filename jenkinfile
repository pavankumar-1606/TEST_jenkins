pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'echo "Starting build process..."'
                bat 'echo "Build completed successfully."'
            }
        }
        stage('Test') {
            steps {
                bat 'echo "Running unit tests..."'
                bat 'echo "All tests passed successfully!"'
            }
        }
        stage('Deploy') {
            steps {
                bat 'echo "Deploying application to environment..."'
                bat 'echo "Deployment successful!"'
            }
        }
        
    }
    
post {
    success {
        emailext(
            subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: """
                <h2>Build Successful!</h2>
                <p>Job: ${env.JOB_NAME}</p>
                <p>Build Number: ${env.BUILD_NUMBER}</p>
                <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
            """,
            to: "your-email@gmail.com"
        )
    }

    failure {
        emailext(
            subject: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: """
                <h2>Build Failed!</h2>
                <p>Job: ${env.JOB_NAME}</p>
                <p>Build Number: ${env.BUILD_NUMBER}</p>
                <p>Check the console output: <a href="${env.BUILD_URL}console">${env.BUILD_URL}console</a></p>
            """,
            to: "your-email@gmail.com"
        )
    }
}

}
