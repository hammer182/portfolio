pipeline {

    environment {
        dockerimagename = "maarcoalr/portfolio2"
        dockerImage = ""
    }

    agent any

    stages{
        stage('Fetch code') {
            steps {
                git branch: 'main', url: 'https://github.com/hammer182/portfolio.git'
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