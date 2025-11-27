pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ezioraz/static-website-cicd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t static-site:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker rm -f static-container || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d --name static-container -p 8080:80 static-site:latest
                '''
            }
        }
    }
}
