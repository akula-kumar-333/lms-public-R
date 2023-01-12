pipeline {
    agent any
    stages {
        stage('Build on Jenkins Server') {
            steps {
                echo 'Building on Jenkins Server'
                sh 'docker image ls'
            }
        }
        stage('Deploy to Slave') {
            agent {
                label 'docker'
            }
            steps {
                echo 'Deploying to slave...'
                sh 'sudo docker run -dt -p 5432:5432 --network lmsnetwork -e POSTGRES_PASSWORD=password --name lmspgdb postgres'
            }
        }
    }
}

