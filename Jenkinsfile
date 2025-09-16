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
                sh 'docker tag image1 naveenk96/paytm:bank'
            }
        }
        stage('Push') {
            steps {
                script {
                     withDockerRegistry(credentialsId: '45b72e09-1e3d-490d-9b30-d29138d7b732') {
                        sh 'docker push naveenk96/paytm:bank'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 naveenk96/paytm:bank'
            }
        }
    }
}
