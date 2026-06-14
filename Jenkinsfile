pipeline {
    agent any

    environment {
        AWS_REGION = 'ap-south-1'

        ECR_REPO = 'jenkins-docker-aws-ecs'

        ECR_URI = '994114819080.dkr.ecr.ap-south-1.amazonaws.com/jenkins-docker-aws-ecs'

        IMAGE_TAG = "${BUILD_NUMBER}"

        ECS_CLUSTER = 'python-cluster'

        ECS_SERVICE = 'python-service'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/AbhiSarin/Jenkins-Docker-AWS_ECS.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $ECR_REPO:$IMAGE_TAG .
                '''
            }
        }

        stage('Login To ECR') {
            steps {
                sh '''
                aws ecr get-login-password \
                --region $AWS_REGION \
                | docker login \
                --username AWS \
                --password-stdin $ECR_URI
                '''
            }
        }

       stage('Push Docker Image') {
    steps {
        sh '''
        docker tag ${IMAGE_NAME}:${IMAGE_TAG} ${ECR_URI}:${IMAGE_TAG}
        docker tag ${IMAGE_NAME}:${IMAGE_TAG} ${ECR_URI}:latest

        docker push ${ECR_URI}:${IMAGE_TAG}
        docker push ${ECR_URI}:latest
        '''
    }
}

        stage('Deploy To ECS') {
            steps {
                sh '''
                aws ecs update-service \
                --cluster $ECS_CLUSTER \
                --service $ECS_SERVICE \
                --force-new-deployment
                '''
            }
        }
    }
}