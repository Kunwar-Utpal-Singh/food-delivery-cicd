pipeline {
    agent { label 'build-agent' }

    stages {
        stage('Pull Source Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Kunwar-Utpal-Singh/food-delivery-cicd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t food-delivery-app:latest .'
            }
        }

        stage('Run Test Container') {
            steps {
                sh '''
                docker rm -f food-delivery-app || true
                docker run -d --name food-delivery-app -p 8081:80 food-delivery-app:latest
                '''
            }
        }
    }
}
