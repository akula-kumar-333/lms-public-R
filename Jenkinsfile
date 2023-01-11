pipeline {
    agent { node { label 'lms' } }
    stages {
        stage('Build backend') {
            steps {
                echo 'Building...'
                sh 'cd api'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}

