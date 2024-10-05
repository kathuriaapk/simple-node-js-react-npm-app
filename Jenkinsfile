pipeline {
    agent any

    environment {
        GIT_REPO_URL = 'https://github.com/kathuriaapk/simple-node-js-react-npm-app' // Update with your repository URL
    }

    stages {
        stage('Input Branch') {
            steps {
                script {
                    // Ask the user to input the branch name
                    BRANCH = input(
                        id: 'userInput', message: 'Enter the branch to build:', 
                        parameters: [string(defaultValue: 'main', description: 'Branch to checkout', name: 'Branch')]
                    )
                }
            }
        }

        stage('Checkout') {
            steps {
                // Checkout the code from the inputted branch
                echo "Checking out branch: ${BRANCH}"
                git branch: BRANCH, url: GIT_REPO_URL
            }
        }
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Test') { 
            steps {
                sh './jenkins/scripts/test.sh' 
            }
        }
    }
}