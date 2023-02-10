pipeline
{
    agent any
    stages {
        stage('build step'){
            steps{
                script {
                    def customImage = docker.build("test-image:${env.BUILD_ID}","-f nginx/Dockerfile .")
                }
            }
        }
        stage('Push image') {
            steps{
                script{
                    withDockerRegistry([ credentialsId: "Khachik01", url: "https://hub.docker.com/repository/docker/khachik01/" ]) {
                    customImage.push()
                }
            }
        }
    }    
    }
}