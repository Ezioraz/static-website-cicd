pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t static-site:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f static-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name static-container -p 8081:80 static-site:latest'
            }
        }
    }
}
