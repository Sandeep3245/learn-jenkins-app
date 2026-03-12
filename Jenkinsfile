pipeline {
    // 1. THE AGENT CHANGE: We tell Jenkins to build the kitchen first!
    agent {
        docker { 
            image 'node:18-alpine' 
        }
    }
    
    environment {
        CI = 'true'
    }

    stages {
        stage('build') {
            steps {
                // 2. THE COMMAND CHANGE: We use 'sh' because the container is running Linux
                bat 'npm ci'
                bat 'npm run build'
            }
        }
        
        stage('test') {
            steps {
                bat 'npm test -- --passWithNoTests'
            }
        }
        
        stage('verify build') {
            steps {
                script {
                    // This is a Jenkins command, so it stays exactly the same!
                    if (fileExists('build/index.html')) {
                        echo '✅ ASSIGNMENT PASSED: index.html was found successfully!'
                    } else {
                        error '❌ ASSIGNMENT FAILED: index.html is missing!'
                    }
                }
            }
        }
    }
}