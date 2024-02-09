pipeline {
    agent any
    stages {
        stage('Clone Repository'){
            steps {
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
                sh './api-server'
            }
        }
    }
}
