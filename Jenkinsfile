pipeline {
    agent any

    environment {
        GITHUB_TOKEN = '<L_TOKEN_DYALK>' 
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: "https://${GITHUB_TOKEN}@github.com/ELBARGUIMOHAMED/Portfolio.git", branch: 'main'
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
