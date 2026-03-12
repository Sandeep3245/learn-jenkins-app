pipeline {
    agent any 

    stages {
        stage('build') {
            agent{
                docker{
                    image 'node:18-alpline'
                    reuseNode true

                }
            }
            steps {
             bat '''
                       ls -la
                       node --version
                       npm --version
                       npm ci
                       npm run build
                       ls -la
                '''
                
            }
        }
    }
}