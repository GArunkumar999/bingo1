pipeline{
    agent any
    stages{
        stage('clean workspace'){
            steps{
                cleanWs()
            }
        }
        stage('git clone from scm'){
            steps{
                git branch: 'main', url: 'https://github.com/GArunkumar999/bingo1.git'
            }
            
        }
        stage('install dependencies'){
            steps{
                sh 'npm install'

            }
        }
        stage('docker build and push'){
            steps{
                withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/') {
                 sh 'docker build -t bingo-app:latest .'
                 sh 'docker tag bingo-app:latest arun596/bingo-app:latest'
                 sh 'docker push arun596/bingo-app:latest'
                 sh 'docker rmi arun596/bingo-app:latest'
                }

            }
        }
        stage('run container'){
            steps{
                sh 'docker run -d --name bingo-app -p 3000:3000 arun596/bingo-app:latest'
            }
        }
    }
}
