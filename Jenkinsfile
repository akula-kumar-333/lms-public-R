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
        stage('Deploying on k8s...') {
            agent {
                label 'k8s'
            }
            steps {
                sh 'kubectl apply -f Deployment-DB.yml'
                sh 'kubectl apply -f Deployment-BE.yml'
                sh 'kubectl apply -f Deployment-FE.yml'
                sh 'kubectl apply -f Service.yml'
           
  }
 }
}
}
