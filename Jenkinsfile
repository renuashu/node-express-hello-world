pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/renuashu/node-express-hello-world.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t renukadocker26/my-express-app:$BUILD_NUMBER .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'docker login -u $DOCKER_USER -p $DOCKER_PASS'
                    sh 'docker push <your-dockerhub-username>/my-express-app:$BUILD_NUMBER'
                }
            }
        }
    }
}
