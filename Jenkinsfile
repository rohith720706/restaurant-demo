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
                bat 'docker build -t restaurant-app .'
            }
        }

        stage('Remove Old Container') {
            steps {
                bat 'docker rm -f restaurant >nul 2>&1 || exit 0'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 8085:80 --name restaurant restaurant-app'
            }
        }
    }
}
