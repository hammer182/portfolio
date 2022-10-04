pipeline {

    environment {
        dockerimagename = "maarcoalr/tekever_challenge"
        dockerImage = ""
    }

    agent any

    stages{
        stage('Fetch code') {
            steps {
                git branch: 'main', url: 'https://github.com/hammer182/tekever-challenge'
            }
        }

        stage('Build Docker Image') {
            steps{
                script{
                    dockerImage = docker.build dockerimagename + ":V.$BUILD_NUMBER"
                }
            }
        }
        
    }
}