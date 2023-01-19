pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building backend on Jenkins Server'
                sh 'cd api && docker build -t akulakumar333/lmsbe .'
                echo 'Building frontend on Jenkins Server'
                sh 'cd webapp && docker build -t akulakumar333/lmsfe .'
            }
        }
        stage('Push Image') {
            steps {
                withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
                    sh 'docker push akulakumar333/lmsbe'
                    sh 'docker push akulakumar333/lmsfe'
                }
            }
        }
        stage('Deploy') {
            agent {
                label 'docker'
            }
            steps {
                echo 'Deploying to slave....'
                //sh 'docker run -p 8080:8080 akulakumar333/lmsbe'
            }
        }
    }
}

