pipeline {
    agent { node { label 'lms' } }
    stages {
        stage('Build backend') {
            steps {
                echo 'Building...'
                sh 'cd api && npm install'
                sh 'cd api && npm run build'
            }
        }
        stage('prisma') {
            steps {
                echo 'pm2 steps...'
                sh 'cd api && sudo npm install -g pm2'
                sh 'cd api && npx prisma db push'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}

