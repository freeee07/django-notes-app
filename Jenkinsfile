@Library("Shared") _
pipeline {
    agent { label "vinod" }

    stages {
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }

        stage("Code") {
            steps {
                script{
                    clone("https://github.com/freeee07/django-notes-app.git","main")
                }
            }
        }

        stage("Build") {
            steps {
                script{
                    docker_build("notes-app","latest","freeee07")
                }
            }
        }

        stage("Push to DockerHub") {
            steps {
                script{
                    docker_push("notes-app", "latest", "fireeee07")
                }
            }
        }

        stage("Test") {
            steps {
                echo "This is testing the code"
            }
        }

        stage("Deploy") {
            steps {
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}

