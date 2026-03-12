pipeline {
    agent any 
    
    // Prevents React from hanging forever in watch mode
    environment {
        CI = 'true'
    }

    stages {
        stage('build') {
            steps {
                // IMPORTANT: You must have both commands here!
                bat '''
                    npm ci
                    npm run build
                '''
            }
        }
        
        stage('test') {
            steps {
                // Tells the testing tool not to fail if test files are missing
                bat 'npm test -- --passWithNoTests'
            }
        }
        
        stage('verify build') {
            steps {
                script {
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