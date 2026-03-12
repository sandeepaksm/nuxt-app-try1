pipeline {
    agent any

    tools {
        // Make sure 'node' is configured in Jenkins Global Tool Configuration
        nodejs 'node' 
    }

    environment {
        // CI environment variable to ensure non-interactive builds
        CI = 'true'
    }

    stages {
        stage('Checkout') {
            steps {
                // Pulls code from your GitHub repository
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies using pnpm...'
                // Using pnpm as seen in your project structure
                sh 'npm install -g pnpm'
                sh 'pnpm install'
            }
        }

        stage('Build Nuxt App') {
            steps {
                echo 'Building the Nuxt.js application...'
                sh 'pnpm run build'
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Archive the output folder (usually .output or dist)
                archiveArtifacts artifacts: '.output/**', fingerprint: true
                echo 'Build complete and artifacts archived.'
            }
        }
    }

    post {
        always {
            cleanWs() // Clean workspace after build
        }
        success {
            echo 'Build Successful!'
        }
        failure {
            echo 'Build Failed. Please check logs.'
        }
    }
}
