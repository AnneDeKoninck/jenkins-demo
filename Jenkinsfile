pipeline {
    agent any

     triggers {
        githubPush()
    }
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fastapi-image .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f fastapi-app-container || true'
                sh 'docker run -d --name fastapi-app-container -p 8083:80 fastapi-image'
            }
        }
    }
}
