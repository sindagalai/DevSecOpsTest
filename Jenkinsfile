pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupère le code depuis le dépôt
                checkout scm
            }
        }

        stage('SAST Analysis') {
            steps {
                // Exécuter l'analyse SAST avec SonarQube
                echo 'Running SAST analysis...'
                script {
                    // Exemple avec SonarQube
                    sh 'mvn clean install sonar:sonar -Dsonar.projectKey=my_project -Dsonar.host.url=http://localhost:9000 -Dsonar.login=your_sonarqube_token'
                }
            }
        }
    }
    
    post {
        success {
            echo 'SAST analysis completed successfully.'
        }

        failure {
            echo 'SAST analysis failed.'
        }
    }
}