pipeline {
    agent any

    environment {
        SONARQUBE_ENV = 'SonarQube'  // Ensure this matches your configuration name in Jenkins
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
                    sh 'sonar-scanner -Dsonar.login=squ_e09dcbc62de4d056bb07f789aac7bb32740efe45'
                }
            }
        }
    }
}
