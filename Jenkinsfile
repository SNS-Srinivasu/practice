pipeline {
    agent any

    environment {
        SONARQUBE_ENV = 'MySonarQube' // Replace with your actual SonarQube server name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/SNS-Srinivasu/practice.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE_ENV}") {
                    sh '''
                        sonar-scanner \
                          -Dsonar.projectKey=practice \
                          -Dsonar.sources=. \
                          -Dsonar.host.url=$SONAR_HOST_URL \
                          -Dsonar.login=$SONAR_AUTH_TOKEN
                    '''
                }
            }
        }
    }

    post {
        always {
            echo 'Demo pipeline completed.'
        }
    }
}
