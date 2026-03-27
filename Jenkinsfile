pipeline {
    agent any

    environment {
        IMAGE = "nourhb/web-app:latest"
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/nourhb/k8s-app.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }

    }
}
