pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building on Jenkins Server'
                sh 'cd api && docker build -t akulakumar333/lmsbe .'
            }
        }
        stage('Push Image') {
            steps {
                withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
                    sh 'docker push akulakumar333/lmsbe'
                }
            }
        }
        stage('Deploy') {
            agent {
                label 'docker'
            }
            steps {
                echo 'Deploying to slave....'
                sh 'docker run -p 8080:8080 akulakumar333/lmsbe'
            }
        }
    }
}

