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
                    sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
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

