def customImage
pipeline
{
    agent any
    stages {
        stage('build step'){
            steps{
                script {
                     customImage = docker.build("khachik01/test-image:${env.BUILD_ID}","-f nginx/Dockerfile .")
                }
            }
        }
        stage('Push image') {
            steps{
                script{
                    withDockerRegistry([ credentialsId: "dockerhub", url: " https://index.docker.io/v1/" ]) {
                    customImage.push()
                }
            }
        }
    }    
    }
}