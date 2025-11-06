pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            args '-p 3000:3000'
        }
    }

    environment {
        GITHUB_TOKEN = credentials('GitHubCredential') 
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'GitHubCredential', url: 'https://github.com/ELBARGUIMOHAMED/Portfolio.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Portfolio') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy to GitHub Pages') {
            steps {
                sh '''
                    git config --global user.email "barguim99@gmail.com"
                    git config --global user.name "MOHAMED ELBARGUI"
                    npm run deploy
                '''
            }
        }
    }
}
