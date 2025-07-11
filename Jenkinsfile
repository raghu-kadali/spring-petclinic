pipeline {
    agent any 
    environment {
        SONAR_SERVER= 'spring'
    }

    tools {
        maven 'maven-3.8.9'
    }

    stages {

        stage('Build') {
            steps {
                echo "Starting Maven Build..."
                sh 'mvn clean install'
            }
        }
        stage('Sonar Analysis') {
            steps {
                withSonarQubeEnv("${SONAR_SERVER}") {
                    sh "mvn clean verify sonar:sonar \
                      -Dsonar.login=sqp_eaaf36afe3e6db1ab6094604126b863604458c56"
                }
                
            }
        }
    }

    post {
        always {
            echo '🎉 Build process completed (success or failure)'
        }
    }
}
