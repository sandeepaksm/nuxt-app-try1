pipeline {
    agent any

    tools {
        // This MUST match the 'Name' field in your Global Tool Configuration
        nodejs 'node' 
    }

    stages {
        stage('Verify Tools') {
            steps {
                echo 'Checking Node and NPM versions...'
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Install pnpm') {
            steps {
                echo 'Installing pnpm globally...'
                sh 'npm install -g pnpm'
            }
        }

        stage('Build Nuxt App') {
            steps {
                echo 'Installing dependencies and building...'
                sh 'pnpm install'
                sh 'pnpm run build'
            }
        }
    }

    post {
        always {
            echo 'Nuxt Build Attempt Finished.'
        }
    }
}
