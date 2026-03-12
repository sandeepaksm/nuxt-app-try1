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
    }
}
