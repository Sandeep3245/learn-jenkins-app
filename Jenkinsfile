pipeline {
    // Note: If you have a mix of Linux and Windows nodes, change 'any' 
    // to a label like label 'windows' to ensure it routes correctly.
    agent any 

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                // Using 'bat' instead of 'sh' for Windows CMD
                bat 'echo ✅ Successfully fetched code from SCM to Windows!'
            }
        }
        stage('Test SCM Trigger') {
            steps {
                bat 'echo ✅ Pipeline was successfully triggered by an SCM event!'
                // Printing the workspace directory using Windows environment variables
                bat 'echo Current workspace: %WORKSPACE%'
            }
        }
    }
    post {
        always {
            bat 'echo Windows pipeline test complete.'
        }
    }
}