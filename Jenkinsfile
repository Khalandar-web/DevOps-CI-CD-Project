pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo "Checking out the code"
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building a Docker Image'
                sh 'docker build -t devops-web:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                echo 'Deploy the Image'
                sh '''
                docker stop devops-web || true
                docker rm devops-web || true
                docker run -d -p 9090:80 --name devops-web devops-web:latest
                '''
            }
        }
    }
}
