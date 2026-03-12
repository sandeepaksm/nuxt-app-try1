pipeline {
    agent any

    tools {
	nodejs 'node'
    }
	
    stages {
	stage('Install Node.js') {
            steps {
                echo 'Jenkins is now ensuring Node.js is installed and added to PATH...'
                
                // These commands confirm the installation was successful
                sh 'node -v'
                sh 'npm -v'
            }
        }


	stage('Install pnpm') {
            steps {
                echo 'Installing pnpm via npm (Bypassing Corepack)...'
                // This is the most stable way in Jenkins
                sh 'npm install -g pnpm'
                sh 'pnpm -v'
            }
        }
        stage('Project Dependencies') {
            steps {
                echo 'Installing Nuxt project dependencies...'
                // This looks for your package.json and pnpm-lock.yaml
                sh 'pnpm install --no-optional --ignore-scripts'
            }
        }
        stage('Build Nuxt') {
            steps {
                echo 'Starting Production Build...'
                // Generates the .output folder for deployment
                sh 'pnpm run build'
            }
        }

    }
}
