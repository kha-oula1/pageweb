pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git repository
                git branch: 'main', url: 'https://github.com/kha-oula1/pageweb.git'
            }
        }
        stage('Deploy') {
            steps {
                // Pull Docker images
                sh 'docker pull belhadjkhaoula07900/page_web:latest'
                sh 'docker pull nginx:latest'
                
                // Start services using Docker Compose
                sh 'docker-compose up -d'
            }
        }
        stage('Push to GitHub') {
            steps {
                // Add and commit changes
                sh 'git add .'
                sh 'git commit -m "Update deployment"'
                
                // Push changes to GitHub
                sh 'git push origin main'
            }
        }
    }
}
