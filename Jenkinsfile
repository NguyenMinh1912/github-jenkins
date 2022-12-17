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
               app = docker.build("getintodevops/hellonode")
        }
        stage('Deploy our image') { 
            docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                app.push("getintodevops/hellonode")
                app.push("latest")
            }
        } 
    }
}