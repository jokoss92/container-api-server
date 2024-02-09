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
     post {
            always {
                echo 'Jobs triggered'
                discordSend description: "Jenkins Pipeline Build", footer: "Jobs triggered", link: env.BUILD_URL, result: currentBuild.currentResult, title: JOB_NAME, webhookURL: "https://discord.com/api/webhooks/1205535354665443489/OyGBhMDMJhZ5Y7xfdc7HYjUzLCsgLrbnGHtWB2Gt7oRiVXSZ9wDc0m5WvcX91c8YdEYZ"
            }
            success {
                 echo 'Jobs success'
                 discordSend description: "Jenkins Pipeline Build", footer: "Jobs success", link: env.BUILD_URL, result: currentBuild.currentResult, title: JOB_NAME, webhookURL: "https://discord.com/api/webhooks/1205535354665443489/OyGBhMDMJhZ5Y7xfdc7HYjUzLCsgLrbnGHtWB2Gt7oRiVXSZ9wDc0m5WvcX91c8YdEYZ"
            }
            failure {
                echo 'Jobs failure'
                discordSend description: "Jenkins Pipeline Build", footer: "Jobs failure", link: env.BUILD_URL, result: currentBuild.currentResult, title: JOB_NAME, webhookURL: "https://discord.com/api/webhooks/1205535354665443489/OyGBhMDMJhZ5Y7xfdc7HYjUzLCsgLrbnGHtWB2Gt7oRiVXSZ9wDc0m5WvcX91c8YdEYZ"
            }
            aborted {
                echo 'Jobs aborted'
                discordSend description: "Jenkins Pipeline Build", footer: "Jobs aborted", link: env.BUILD_URL, result: currentBuild.currentResult, title: JOB_NAME, webhookURL: "https://discord.com/api/webhooks/1205535354665443489/OyGBhMDMJhZ5Y7xfdc7HYjUzLCsgLrbnGHtWB2Gt7oRiVXSZ9wDc0m5WvcX91c8YdEYZ"
            }
        }
}
