pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Tests the SCM checkout process
                checkout scm
                echo "✅ Successfully fetched code from SCM!"
            }
        }
        stage('Test SCM Trigger') {
            steps {
                // Proves the pipeline is running
                echo "✅ Pipeline was successfully triggered by an SCM event!"
                sh 'echo "Current workspace: $(pwd)"'
            }
        }
    }
    post {
        always {
            echo "Pipeline test complete."
        }
    }
}