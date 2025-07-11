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
                      -Dsonar.login=sqp_c3cb7c4176aa55994b2d506b31878a646e34c7fd"
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
