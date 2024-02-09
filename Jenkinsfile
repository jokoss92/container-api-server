pipeline {
    agent {
    // Install the desired Go version
    def root = tool name: 'Go 1.20', type: 'go'

    // Export environment variables pointing to the directory where Go was installed
    withEnv(["GOROOT=${root}", "PATH+GO=${root}/bin"]) {
        sh 'go version'
        }
    }
    environment {
        name = 'container-api-server'
    }
    stages {
        stage('Info') {
            steps {
                echo 'Pipeline name: $name'
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
                sh './api-server'
            }
        }
    }
}
