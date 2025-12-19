pipeline {
    agent any

    stages {

        stage('Code Checkout') {
            steps {
                git 'https://github.com/<username>/<repo>.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-jenkins-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker rm -f python_app || true
                docker run -d -p 5000:5000 --name python_app python-jenkins-app
                '''
            }
        }
    }
}
