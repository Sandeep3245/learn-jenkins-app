pipeline {
    agent any 
    
    environment {
        CI = 'true'
    }

    stages {
        stage('build') {
            steps {
                // Using separate bat steps guarantees Windows runs both!
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
                    // Reminder: If this still fails after npm run build executes, 
                    // change 'build/index.html' to 'dist/index.html'
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