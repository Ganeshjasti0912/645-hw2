pipeline {
    agent any

    environment {
        IMAGE_NAME = "ganesh0912/student-survey"
        KUBECONFIG = "/var/lib/jenkins/.kube/config"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Ganeshjasti0912/645-hw2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME:latest .'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'c1d9192e-d276-4541-8fab-ece2f3ec681d',  // your Jenkins Docker creds ID
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS'
                    )
                ]) {
                    script {
                        sh '''
                        echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                        docker push $IMAGE_NAME:latest
                        '''
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'kubectl apply -f hw1-deployment.yaml'
                    sh 'kubectl apply -f hw1-service.yaml'
                }
            }
        }
    }
}
