pipeline {
    agent any

    tools {
        sonarRunner 'SonarScanner'  // This must match the name configured in Global Tool Configuration.
    }

    environment {
        SONARQUBE_ENV = 'SonarQube'  // This should match the SonarQube server name configured in Jenkins.
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
