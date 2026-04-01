pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/AtharvSatao/devops-ci-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop my-app || true
                docker rm my-app || true
                docker run -d -p 8085:80 --name my-app my-app
                '''
            }
        }
    }
}
