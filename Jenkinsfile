pipeline {
    agent any

    environment {
        IMAGE = "nourhb/web-app:latest"
    }

    stages {
stage('Clone') {
    steps {
        git branch: 'main', url: 'https://github.com/nourhb/k8s-app.git'
    }
}

        stage('Build Image') {
            steps {
                sh 'docker build -t nourhb/web-app:latest .'
            }
        }

        stage('Login DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $IMAGE'
            }
        }
    }
}
