pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building on VM'
                sh 'cd webapp'
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying.....'
            }
        }
    }
}
