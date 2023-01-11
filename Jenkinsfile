pipeline {
    agent { node { label 'lms' } }
    stages {
        stage('Build backend') {
            steps {
                echo 'Building...'
                sh 'cd /home/ubuntu/workspace/LMS Project/api'
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

