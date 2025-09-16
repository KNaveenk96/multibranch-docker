pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image2 naveenk96/paytm:bus'
            }
        }
        stage('Push') {
            steps {
                script {
                     withDockerRegistry(credentialsId: '45b72e09-1e3d-490d-9b30-d29138d7b732') {
                        sh 'docker push naveenk96/paytm:bus'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus-app -p 2222:80 naveenk96/paytm:bus'
            }
        }
    }
}
