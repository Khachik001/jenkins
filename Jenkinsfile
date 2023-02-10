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
    }
}