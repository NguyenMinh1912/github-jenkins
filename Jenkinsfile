pipeline { 
    environment { 
        registry = "minhnc111/hello-image" 
        registryCredential = 'dockerhub' 
        dockerImage = 'minhnc111/hello-image:v0' 
    }
    agent any 
    stages { 
        stage('Cloning our Git') { 
            steps { 
                git 'https://github.com/NguyenMinh1912/github-jenkins.git' 
            }
        } 
        stage('Building our image') { 
            steps { 
                script { 
                    dockerImage = docker.build registry + ":v1" 
                }
            } 
        }
        stage('Deploy our image') { 
            steps { 
                script { 
                    docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push() 
                    }
                } 
            }
        } 
        stage('Cleaning up') { 
            steps { 
                sh "docker rmi $registry:v1" 
            }
        } 
    }
}