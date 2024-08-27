pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/NIBI23/microservices-demo.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                script {
                    docker.build("service-a", "./service-a")
                    docker.build("service-b", "./service-b")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        docker.image('service-a').push('latest')
                        docker.image('service-b').push('latest')
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}

