pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
               git branch: 'main', credentialsId: 'mytoken', url: 'https://github.com/kha-oula1/pageweb.git'
            }
        }
        
        stage('Test html site') {
            steps {
                  publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'jen.html', reportName: 'HTML Report',                   reportTitles: '', useWrapperFileDirectly: true])
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker pull belhadjkhaoula07900/page_web:latest'
                sh 'docker pull nginx:latest'
                sh 'docker-compose up -d'
            }
        }
        
        stage('Push to GitHub') {
            steps {
                sh 'git add .'
                sh 'git commit -m "Jenkinsfile"'
                sh 'git push'
            }
        }
    }
}

