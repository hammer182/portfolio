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
                    dockerImage = docker.build dockerimagename + ":v.$BUILD_NUMBER"
                }
            }
        }

        stage('Push image to DockerHub') {
            environment {
                registryCredential = 'dockerhub'    
            }
            steps {
                script {
                    docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
                        dockerImage.push("v.$BUILD_NUMBER")
                        dockerImage.push("latest")
                    }
                }
            }
        }
        
    }
}