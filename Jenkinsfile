pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git credentialsId: 'gitcred', url: 'https://github.com/ROGAN07sg/tictactoe.git'
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
    }
}
