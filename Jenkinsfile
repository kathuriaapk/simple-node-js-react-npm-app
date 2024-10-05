pipeline {
    agent any

    environment {
        GIT_REPO_URL = 'https://github.com/kathuriaapk/simple-node-js-react-npm-app' // Update with your repository URL
    }

    parameters {
        string(name: 'BRANCH', defaultValue: 'master', description: 'Branch to build')  // Reference the branch parameter
    }

    stages {

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