pipeline {
    agent { node { label 'lms' } }
    stages {
        stage('Build backend') {
            steps {
                echo 'Building backend'
                sh 'cd api && npm install'
                sh 'cd api && npm run build'
            }
        }
        stage('prisma') {
            steps {
                echo 'pm2 steps...'
                sh 'cd api && sudo npm install -g pm2'
                sh 'cd api && npx prisma db push'
                sh 'cd api && -f NODE_PORT=8080 pm2 start -i 0 build/index.js'
            }
        }
        stage('Build frontend') {
            steps {
                echo 'Building frontend'
                sh 'cd webapp && npm install'
                sh 'cd webapp && npm run build'
            }
        }
    }
}

