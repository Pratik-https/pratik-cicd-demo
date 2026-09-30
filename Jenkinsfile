pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'python -m pytest -q'
            }
        }

        stage('Deploy') {
            steps {
                bat 'if not exist deployment mkdir deployment'
                bat 'copy /Y app.py deployment\\app.py'
                bat 'copy /Y requirements.txt deployment\\requirements.txt'
                bat 'echo Deployment completed for Pratik Haladkar'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully - Pratik Haladkar'
        }

        failure {
            echo 'CI/CD Pipeline failed. Check the build logs.'
        }
    }
}