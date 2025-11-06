pipeline {
    agent any

    environment {
        GITHUB_TOKEN = credentials('Token')
        REPO_URL = 'https://github.com/ELBARGUIMOHAMED/Portfolio.git'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', credentialsId: 'Token', url: "${REPO_URL}"
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

