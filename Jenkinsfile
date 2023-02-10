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
                       sshagent(credentials:['ssh_connect']){
                      sh 'ssh  -o StrictHostKeyChecking=no  ubuntu@3.235.128.124 touch ~/hello'
                      
                     // sh """
                // docker run -d  khachik01/test-image:${env.BUILD_ID}
                // """
            }
            sh 'touch ~/hello'
            }
        }    
    }
}