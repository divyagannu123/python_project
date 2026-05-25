pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                sh '''
                rm -rf venv
                python3 -m venv venv
                chmod -R 755 venv

                ./venv/bin/python -m pip install --upgrade pip
                ./venv/bin/python -m pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                ./venv/bin/python -m pytest
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-app .'
            }
        }

    }
}
