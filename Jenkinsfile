pipeline {
    agent any 
     environment {
        DockerHub = credentials('dockerHub')
    }
    stages{
        stage("Clone Code"){
            steps {
                echo "Cloning the code"
                git url:"https://github.com/suraj1517/dockerfile.git", branch: "master"
            }
        }
        stage("Build"){
            steps {
                echo "Building the image"
                sh "docker build -t my-nginx-image ."

            }
        }
                stage("Push to Docker Hub"){
            steps {
                echo "Pushing the image to docker hub"
                withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")])
                {
                  
                     sh("curl -u ${dockerHubUser}:${dockerHubPass} https://hub.docker.com/")
                     
                     
                     
                }
            }
        }
    }
}
