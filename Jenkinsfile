pipeline {
    agent { node { label 'lms' } }
    stages {
        stage('Build backend') {
            steps {
                echo 'Building...'
                sh 'cd workspace/LMS Project/api'
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

