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
        stage('login server'){
            steps{
                
                sshagent(credentials:['ubuntu']){
                sh 'ssh  -o StrictHostKeyChecking=no  ubuntu@ec2-3-236-204-86.compute-1.amazonaws.com uptime "whoami"'
                
            }
             echo "success login"
            }
        }    
    }
}