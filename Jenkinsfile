pipeline {
    agent any

    environment {
        SONARQUBE_ENV = 'MySonarQube' // Replace with your configured SonarQube server name
    }

    tools {
        sonarScanner 'SonarQube' // Replace with the name you used in Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/SNS-Srinivasu/practice.git'
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
