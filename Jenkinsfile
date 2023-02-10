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
        withDockerRegistry([ credentialsId: "Khachi01", url: "https://hub.docker.com/repository/docker/khachik01/aca_homework/general" ]) {
        dockerImage.push()
        }
    }    
    }
}