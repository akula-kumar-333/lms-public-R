pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building on VM'
                sh 'cd webapp && npm install'
                sh 'cd webapp && npm run build'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying..........'
            }
        }
    }
}
