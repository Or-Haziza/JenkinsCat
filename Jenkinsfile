pipeline {
 agent any
    environment {
        AWS_ACCOUNT_ID="992382545251"
        AWS_DEFAULT_REGION="us-east-1"
        IMAGE_REPO_NAME="or"
        IMAGE_TAG="v1"
        REPOSITORY_URI = "992382545251.dkr.ecr.us-east-1.amazonaws.com/or"
        DOCKER_HOST = "tcp://172.18.0.3:2375"
    }
   
    stages {
        stage('ECR Login') {
            steps {
                script {
                    sh """aws --version"""
                   
                    sh """aws ecr get-login-password --region ${AWS_DEFAULT_REGION} | docker login --username AWS --password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com"""

                }
            }
        }
        
        
                
        stage('Building image') {
            steps{
                script {
                    sh """docker build -t ${REPOSITORY_URI}:${IMAGE_TAG} ."""
                    }
                }
            }
                    // Uploading Docker images into AWS ECR
        stage('Pushing to ECR') {
            steps{  
                script {
                   
                    sh """docker push ${REPOSITORY_URI}:${IMAGE_TAG}"""
                }
            }
        }
    }
}
