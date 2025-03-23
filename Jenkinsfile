@Library("shared") _
pipeline {
    
    agent {label "agent-v"}
    
    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
            steps{
                script{
                clone("https://github.com/rahoolch/Rahool-django-notes-app.git","main")   
                }
               
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","vrool")
                }
                
            }
            
        }
        stage("Push"){
            steps{
                script{
                    docker_push("notes-app","latest")
                }
                
            }
            
        }
        stage("Deploy"){
            steps{
                echo "Code deploy stage"
                sh "docker compose up -d"
            }
            
        }
    }
}
