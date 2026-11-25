@Library("Shared") _
pipeline {
    
    agent { label "vinod"}
    
    stages{
        
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("code") {
            steps{
                script{
                    echo "This is cloning the code"
                    clone("https://github.com/prasad1702/django-notes-app.git", "main")
                }
            }
        }
        
        stage("build") {
            steps{
                script{
                    echo "This is building the code"
                    docker_build("notes-app", "latest", "prasadsakpal")
                }
                
            }
        }
        
       stage("Push to DockerHub") {
            steps {
                script{
                    push_to_dockerhub("notes-app","latest", "prasadsakpal")
                }
        }
    }
        
        stage("deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }

}
