pipeline {
    agent any 

    stages {
        stage('build') {
            steps {
                // We added npm ci and npm run build here!
                bat '''
                    npm ci
                    npm run build
                '''
            }
        }
        
        stage('test') {
            steps {
                bat 'npm test'
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