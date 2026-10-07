pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/muhammad-saad22/depi-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t muhammad-saad22/nginx-lab:$BUILD_NUMBER .'
            }
        }

        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push muhammad-saad22/nginx-lab:$BUILD_NUMBER'
                }
            }
        }
    }
}
