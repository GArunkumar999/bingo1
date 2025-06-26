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
                withDockerRegistry(credentialsId: 'dockerhub') {
                 sh 'docker build -t bingo-app:latest .'
                 sh 'docker tag bingo-app:latest arun596/bingo-app:latest'
                 sh 'docker push arun596/bingo-app:latest'
                }

            }
        }
    }
}
