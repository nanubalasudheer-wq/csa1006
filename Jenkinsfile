pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t cicd-demo .'
            }
        }

        stage('Test') {
            steps {
                bat 'docker run --rm cicd-demo nginx -t'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker stop cicd-container || exit 0'
                bat 'docker rm cicd-container || exit 0'
                bat 'docker run -d -p 8081:80 --name cicd-container cicd-demo'
            }
        }
    }
}
