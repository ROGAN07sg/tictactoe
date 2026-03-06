pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git credentialsId: 'gitcred', url: 'https://github.com/ROGAN07sg/tictactoe.git' , branch: 'main'
            }
        }

        stage('Validate') {
            steps {
                sh 'mvn validate'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('docker build') {
            steps {
                sh 'docker build -t ticimg .'
            }
        }
        stage('docker run') {
            steps {
                sh '''
                     docker stop ticcon || true
                     docker rm ticcon || true
                     docker run -d -p 8081:8080 --name ticcon ticimg
                     '''
            }
        }
        
    }
}
