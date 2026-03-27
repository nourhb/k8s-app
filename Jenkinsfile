pipeline {
    agent any

    environment {
        IMAGE = "yourdockerhub/web-app:latest"
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/nourhb/k8s-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }

        stage('Push to DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push $IMAGE'
                }
            }
        }
    }
}
