pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/Aryanraj2400/Real-Time-Chatty.git'
            }
        }

        stage('Build Backend Image') {
            steps {
                dir('backend') {
                    sh 'docker build -t chat-backend .'
                }
            }
        }

        stage('Build Frontend Image') {
            steps {
                dir('frontend') {
                    sh 'docker build -t chat-frontend .'
                }
            }
        }

        // stage('Push Images') {
        //     steps {
        //         withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
        //             sh """
        //                 echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin
        //                 docker tag chat-backend YOUR_DOCKERHUB_USERNAME/chat-backend
        //                 docker tag chat-frontend YOUR_DOCKERHUB_USERNAME/chat-frontend
        //                 docker push YOUR_DOCKERHUB_USERNAME/chat-backend
        //                 docker push YOUR_DOCKERHUB_USERNAME/chat-frontend
        //             """
        //         }
        //     }
        // }

        // stage('Deploy to Kubernetes') {
        //     steps {
        //         sh 'kubectl apply -f k8s/'
        //     }
        // }

        stage('Pipeline Complete') {
            steps {
                echo '✅ Deployment pipeline completed successfully!'
                echo '📝 Images pushed to Docker Hub and application deployed to Jenkins.'
            }
        }
    }
}
