pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/MohsinMandlik/devops-cicd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop devops-container || exit 0'
                bat 'docker rm devops-container || exit 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 3000:3000 --name devops-container devops-app'
            }
        }
    }
}