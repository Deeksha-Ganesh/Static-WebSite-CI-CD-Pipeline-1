pipeline {
    agent any
    environment {
        DOCKER_HUB_USER = "DockerHubUserName"
        DOCKER_HUB_PASS = "DockerHubPassword"
        IMAGE_NAME = "DockerHubUserName/Image_Name"
        EC2_USER = "ec2-user" // use 'ec2-user' if it's Amazon Linux
        EC2_HOST = "Public Ip" // your EC2 public IP
        PEM_KEY_PATH = "Path of Pem Key"
    }
    stages {
        stage('Clone Repository') {
            steps {
                        git branch: 'main', url: 'https://github.com/Deeksha-Ganesh/Static-WebSite-CI-CD-Pipeline-1.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                sh 'echo $DOCKER_HUB_PASS | docker login -u $DOCKER_HUB_USER --password-stdin'
            }
        }
        stage('Push Image to Docker Hub') {
            steps {
                sh 'docker push $IMAGE_NAME'
            }
        }
        stage('Deploy to EC2') {
            steps {
                sh '''
                    ssh -i $PEM_KEY_PATH -o StrictHostKeyChecking=no $EC2_USER@$EC2_HOST \
                    "docker pull $IMAGE_NAME &&
                    docker rm -f webapp || true &&
                    docker run -d --name webapp -p 80:80 $IMAGE_NAME"
                '''
            }
        }
    }
}
