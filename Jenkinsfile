pipeline {
    agent any
    environment {
        NAME = 'container-api-server'
        TOKEN = credentials('token')
    }
    stages {
        stage('Info') {
            steps {
                echo 'Pipeline name: $NAME'
                sh 'echo $TOKEN >> token.txt'
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
               sh 'docker stop api-server && docker rm api-server && docker rmi api-server'
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
