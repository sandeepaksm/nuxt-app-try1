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

        stage('Setup pnpm') {
            steps {
                echo 'Activating pnpm via Corepack...'
                // Corepack comes with Node 22 and is the recommended way to use pnpm
                sh 'corepack enable'
                sh 'corepack prepare pnpm@latest --activate'
                
                sh 'pnpm -v'
            }
        }

    }
}
