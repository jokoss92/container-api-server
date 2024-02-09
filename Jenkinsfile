pipeline {
    agent any
    environment {
        name = 'container-api-server'
    }
    stages {
        stage('Info') {
            steps {
                echo 'Pipeline name: $name'
                sh 'go version'
            }
        }
        stage('Clone Repository'){
            steps {
                sh 'rm -rf container-api-server'
                sh 'git clone https://github.com/jokoss92/container-api-server.git'
            }
        }
        stage('Build'){
            steps {
               sh 'go build -o api-server '
            }
        }
         stage('Run app'){
            steps {
                sh 'chmod +x api-server'
                sh './api-server &'
            }
        }
    }
}
