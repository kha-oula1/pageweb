pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'mytoken', url: 'https://github.com/kha-oula1/pageweb.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t page_web .'
            }
        }
        
        stage('Test html site') {
            steps {
                 publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'jen.html', reportName: 'HTML Report',reportTitles: '', useWrapperFileDirectly: true])
            }
        }
        
        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8180:80 --name myapp page_web'
            }
        }
        
        stage('Push to Docker Hub') {
            steps {
                sh 'docker login -u belhadjkhaoula07900 -p khaoula@07'
                sh 'docker tag page_web docker.io/belhadjkhaoula07900/page_web:latest'
                sh 'docker push docker.io/belhadjkhaoula07900/page_web:latest'
            }
        }
        
        stage('Deploy with Docker Compose') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}


