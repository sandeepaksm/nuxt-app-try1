pipeline {
    agent any

    tools {
        // This MUST match the name you give in 'Global Tool Configuration'
        nodejs 'node' 
    }

    environment {
        // Ensures pnpm and nuxt run in non-interactive mode
        CI = 'true'
    }

    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                echo 'Workspace cleaned.'
            }
        }

        stage('Checkout Source') {
            steps {
                // Pulls code from your GitHub repository
                checkout scm
            }
        }

        stage('Install pnpm & Dependencies') {
            steps {
                script {
                    echo 'Installing pnpm and project dependencies...'
                    // Ensure pnpm is available on the Jenkins agent
                    sh 'npm install -g pnpm'
                    sh 'pnpm install'
                }
            }
        }

        stage('Build Nuxt Application') {
            steps {
                echo 'Running Nuxt Build...'
                sh 'pnpm run build'
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Archive the production build (usually the .output folder in Nuxt 3)
                archiveArtifacts artifacts: '.output/**', allowEmptyArchive: true
                echo 'Build artifacts have been saved.'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: The Nuxt application was built successfully!'
        }
        failure {
            echo 'FAILURE: The build failed. Check the console output for errors.'
        }
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
