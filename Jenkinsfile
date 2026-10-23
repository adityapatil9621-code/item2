pipeline {
    agent any

    environment {
        PATH = "/Users/aditya/.docker/bin:/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check Docker') {
            steps {
                sh '''
                    echo "Docker path:"
                    command -v docker
                    docker --version
                    docker info
                '''
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
