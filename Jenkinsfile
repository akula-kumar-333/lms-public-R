pipeline {
    agent {
        docker {
            registryUrl 'https://hub.docker.com/u/akulakumar333'
            registryCredentialsId 'docker-hub'
        }
    }
    stages {
        stage('Build on Jenkins Server') {
            steps {
                echo 'Building on Jenkins Server'
                sh 'cd api && docker build -t akulakumar333/lmsbe .'
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

