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
                sh 'docker container rm -f lmspgdb'
                sh 'docker run -dt -p 5432:5432 --network lmsnetwork -e POSTGRES_PASSWORD=password --name lmspgdb postgres'
            }
        }
        stage('Deploying backend') {
            agent {
                label 'docker'
            }
            steps {
                echo 'Running Backend container association with DB'
                sh 'docker run -dt --name lmsback -p 8080:8080 --network lmsnetwork -e DATABASE_URL=postgresql://postgres:password@lmspgdb:5432/postgres -e PORT=8080 -e MODE=local akulakumar333/lmsbe'
    }
  }
        stage('Deploying frontend') {
            agent {
                label 'docker'
            }
            steps {
                echo 'Running Frontend container for finally deploying the complete website'
                sh 'docker container run -dt -p 3000:3000 --name lmsfront akulakumar333/lmsfe'
  }
 }
}
}
