pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t adrios12-website .'
            }
        }

        stage('Test Docker Image') {
            steps {
                sh 'docker image inspect adrios12-website'
                echo 'Docker image built and verified successfully!'
            }
        }
    }

    post {
        success {
            echo 'Jenkins CI/CD pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
