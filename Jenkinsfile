pipeline {

    agent any

    environment {
        IMAGE_NAME = "enterprise"
    }

    stages {

        stage('Clone') {
            steps {
                echo 'https://github.com/narupallenandu/enterprise-devsecops-pipeline.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $IMAGE_NAME:$BUILD_NUMBER .
                '''
            }
        }

        stage('Syft Scan') {
            steps {
                sh '''
                syft $IMAGE_NAME:$BUILD_NUMBER -o table > syft-report.txt
                '''
            }
        }

        stage('Grype Scan') {
            steps {
                sh '''
                grype $IMAGE_NAME:$BUILD_NUMBER -o table > grype-report.txt
                '''
            }
        }

        stage('DockerHub Login') {
            steps {

                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {

                    sh '''
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    '''
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh '''
                docker push $IMAGE_NAME:$BUILD_NUMBER
                '''
            }
        }

        stage('Upload Reports to AWS S3') {
            steps {

                withAWS(credentials: 'aws-creds', region: 'us-east-1') {

                    sh '''
                    aws s3 cp syft-report.txt s3://your-bucket-name/
                    aws s3 cp grype-report.txt s3://your-bucket-name/
                    '''
                }
            }
        }

        stage('Archive Reports') {
            steps {
                archiveArtifacts artifacts: '*.txt', fingerprint: true
            }
        }
    }
}
