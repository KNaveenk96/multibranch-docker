pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 naveenk96/paytm:movie'
            }
        }
        stage('Push') {
            steps {
                script {
                     withDockerRegistry(credentialsId: '45b72e09-1e3d-490d-9b30-d29138d7b732') {
                        sh 'docker push naveenk96/paytm:movie'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 naveenk96/paytm:movie'
            }
        }
    }
}
