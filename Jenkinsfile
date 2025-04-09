pipeline {
    agent any

    tools {
        nodejs "NodeJS"  // Optional: if you're using NodeJS tool config in Jenkins
    }

    environment {
        SONARQUBE_ENV = 'SonarQube' // Must match the name you gave in Jenkins config
    }

    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE_ENV}") {
                    sh 'sonar-scanner'
                }
            }
        }
    }
}
