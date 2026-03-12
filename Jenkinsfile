pipeline {
    // This tells Jenkins to run the job on any available Jenkins node/machine
    agent any 

    stages {
        stage('build') {
            steps {
                // 'bat' runs these commands on the Windows machine
                bat '''
                    dir
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    dir
                '''
            }
        }
    }
}