pipeline {
    agent any
    stages {
        stage('Build on Jenkins Server') {
            steps {
                echo 'Building on Jenkins Server'
                sh 'cd api && docker build -t akulakumar333/lmsbe .'
            }
        }
        stage('Build and Push to Docker') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh "echo ${DOCKER_PASSWORD} | docker login --password-stdin -u ${DOCKER_USERNAME}"
                    sh "docker push akulakumar333/lmsbe"
                }
            }
        }
        stage('Deploy to Slave') {
            agent {
                label 'docker'
            }
            steps {
                echo 'Deploying to slave...'
            }
        }
    }
}

