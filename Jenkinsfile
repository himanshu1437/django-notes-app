@Library('Shared') _
pipeline{
    agent { label 'vinod'}
    
    stages{
        stage ("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code clone"){
            steps{
               script{
            docker_clone("https://github.com/LondheShubham153/django-notes-app.git","main")
               }
            }
        }
        stage("Code Build"){
            steps{
                script{
            docker_build("notes-app","latest","himanshu52758")
                }
            }
        }
        stage("Code Push to DockerHub"){
            steps{
                script{
                docker_push("notes-app","latest","himanshu52758")
                } 
            }
        }
        stage("Code Deploy"){
            steps{
                echo "This is Deploying The Code"
                sh "docker compose up -d && docker compose up -d"
            }
        }
        
    }
}
