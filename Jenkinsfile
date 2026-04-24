pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/<your-username>/<repo-name>.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t webapp:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker rm -f web-container || true
                docker run -d -p 8080:80 --name web-container webapp:latest
                '''
            }
        }
    }
}
