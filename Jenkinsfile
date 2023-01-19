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
                    echo 'pushing backend image'
                    sh 'docker push akulakumar333/lmsbe'
                    echo 'pushing frontend image'
                    sh 'docker push akulakumar333/lmsfe'
                }
            }
        }
        stage('Deploying DB') {
            agent {
                label 'docker'
            }
            steps {
                echo 'Running DB container with environment variables'
                sh 'docker run -dt -p 5432:5432 --network lmsnetwork -e POSTGRES_PASSWORD=password --name lmspgdb postgres'
            }
        }
    }
}

