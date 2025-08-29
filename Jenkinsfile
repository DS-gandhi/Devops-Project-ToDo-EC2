pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'dev', url: 'https://github.com/DS-gandhi/Devops-Project-ToDo-EC2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t todo-app:latest .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Stop & remove any old container
                    sh 'docker rm -f todo-app || true'

                    // Run new container on port 5000
                    sh 'docker run -d -p 5000:5000 --name todo-app todo-app:latest'
                }
            }
        }
    }
}
