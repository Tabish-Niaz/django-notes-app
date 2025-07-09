@Library("Shared") _
pipeline{
    agent {label "tabish" }
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
               script{
                   clone("https://github.com/Tabish-Niaz/django-notes-app.git","main")
               }
                
            }
        }
        stage("Build"){
            steps{
                
                docker_build("notes-app","latest","tabishniaz247123")
                
            }
        }
        stage("Push to DockerHub"){
            steps{
               script{
                   docker_push("notes-app","latest","tabishniaz247123")
               }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker run -d -p 8000:8000 notes-app:latest"
            }
        }
    }
}
