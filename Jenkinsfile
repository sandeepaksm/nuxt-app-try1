pipeline {
    agent any

    stages {
        stage('Environment Setup') {
            steps {
                echo 'Checking Environment...'
                // Instead of using 'tools', we check manually to avoid the NullPointer
                sh 'node -v || echo "Node not found"'
            }
        }

        stage('Install pnpm') {
            steps {
                // Using standard shell to install pnpm
                sh 'npm install -g pnpm || true'
            }
        }

        stage('Build') {
            steps {
                sh 'pnpm install'
                sh 'pnpm run build'
            }
        }
    }
    
    post {
        always {
            echo 'Finished Nuxt Build Attempt'
        }
    }
}
