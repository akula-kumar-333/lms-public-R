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
                echo 'Deploying..'
                sh 'scp -r webapps/dist ubuntu@172.31.14.26:/home/ubuntu/dist'
            }
        }
    }
}
