pipeline {
    agent any

    environment {
        SONARQUBE_ENV = "server_sonar"
    }
    tools {
        maven 'maven-3.8.9'
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE_ENV}") {
                    sh 'mvn sonar:sonar -Dsonar.projectKey=fresh'
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 30, unit: 'SECONDS') {
                    waitForQualityGate(abortPipeline: true, sonarQube: env.SONARQUBE_ENV)
                }
            }
        }
    }
}
