pipeline {
    agent { label 'docker' }

    environment {
        IMAGE = "myapp:${BUILD_NUMBER}"

        // Docker Hub
        DOCKER_IMAGE = "ashutech517/ansible-job"
        DOCKER_TAG = "${BUILD_NUMBER}"

        // Docker credentials
        DOCKER_CREDS = credentials('dockerhub-creds')
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build local image
                    sh 'docker build -t $IMAGE .'

                    // Tag image for Docker Hub
                    sh 'docker tag $IMAGE ${DOCKER_IMAGE}:${DOCKER_TAG}'
                }
            }
        }

        stage('Unit Test') {
            steps {
                sh 'docker run --rm $IMAGE echo "Running tests..."'
            }
        }

        stage('Docker Login') {
            steps {
                sh '''
                    echo $DOCKER_CREDS_PSW | docker login -u $DOCKER_CREDS_USR --password-stdin
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push ${DOCKER_IMAGE}:${DOCKER_TAG}'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker rm -f myapp || true
                    docker run -d --name myapp -p 8080:80 ${DOCKER_IMAGE}:${DOCKER_TAG}
                '''
            }
        }
    }

    post {

        success {
            echo "Deployment successful and Docker image pushed!"
        }

        failure {
            echo "Pipeline failed!"
        }

        always {
            sh 'docker logout || true'
            sh 'docker system prune -f'
        }
    }
}
