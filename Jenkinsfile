pipeline {
    agent any

    environment {
        PYTHON = 'C:\\Users\\DELL\\AppData\\Local\\Programs\\Python\\Python313\\python.exe'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '"%PYTHON%" -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat '"%PYTHON%" -m pytest -q'
            }
        }

        stage('Deploy') {
            steps {
                bat 'if not exist deployment mkdir deployment'
                bat 'copy /Y app.py deployment\\app.py'
                bat 'copy /Y requirements.txt deployment\\requirements.txt'
                bat 'echo Deployment files prepared for Pratik Haladkar'
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