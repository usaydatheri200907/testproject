pipeline {
    agent any

    environment {
        IMAGE_NAME = 'my-react-app'
        IMAGE_TAG = 'latest'
    }

    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
            }
        }
    }
}
