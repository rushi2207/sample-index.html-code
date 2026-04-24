pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t webapp:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker rm -f web-container || true
                docker run -d -p 8081:80 --name web-container webapp:latest
                '''
            }
        }
    }
}
