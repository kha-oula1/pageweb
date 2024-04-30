pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code depuis le dépôt GitHub
                git 'https://github.com/votre-utilisateur/votre-repo.git'
            }
        }

        stage('Deploy') {
            steps {
                // Tirer l'image Docker 'myapp' depuis Docker Hub
                sh 'docker pull belhadjkhaoula07900/page_web:latest'

                // Tirer l'image Docker 'nginx' depuis Docker Hub
                sh 'docker pull belhadjkhaoula07900/nginx:latest'

                // Exécuter Docker Compose pour déployer les services
                sh 'docker-compose up -d'
            }
        }

        stage('Push to GitHub') {
            steps {
                // Ajouter et committer les modifications
                sh 'git add .'
                sh 'git commit -m "inscription page web"'

                // Poussez les modifications vers le dépôt GitHub
                sh 'git push origin main'
            }
        }
    }
}
