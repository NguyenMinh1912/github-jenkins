pipeline{
    agent any   
    stages{
        stage("Clone Stage"){
            steps{
                git "https://github.com/NguyenMinh1912/github-jenkins.git"
            }
        }

        stage('Build image') {
            steps{
               dockerImage = docker.build("minhnc/hello-image:v1")
            }
        }
    
        stage('Push image') {
            steps{
                withDockerRegistry([ credentialsId: "dockerhub", url: "https://index.docker.io/v1/" ]) {
                    dockerImage.push()
                }
            }
           
        }    
            
        // stage("Build and push docker image"){
        //     steps{
        //         withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/'){
        //             sh 'docker build -t minhnc/hello-image:v1 .'
        //             sh 'docker push'
        //         }
        //     }
        // }
    }
}