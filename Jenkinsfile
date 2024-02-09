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
               sh 'docker build -t api-server .'
            }
        }
         stage('Run app'){
            steps {
                sh 'docker run -d -p 8000:8000 --name api-server api-server'
            }
        }
    }
}
