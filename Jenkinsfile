pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 maheshvte/paytm:bank'
            }
        }
        stage('Push') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'dockerhub creds') {
                    sh 'docker push maheshvte/paytm:bank'
                    }
                }
            }
        }
        
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 maheshvte/paytm:bank'
            }
        }
    }
}
