@Library('Shared') _

pipeline{
    agent { label "kalu" }
    
    stages{
        stage("Code Clone"){
            steps{
                script{
                    echo "Clone Started"
                    clone("https://github.com/anurag1352/reddit-clone-yt.git", "main")
                    echo "Clone Successful."
                }
            }
        }
        stage("Code Build"){
            steps{
               script{
                   echo "Docker Build Started."
                   build("reddit-app", "latest", "anurag904")
               }
            }
        }
        stage("Build Push to DockerHub"){
            steps{
                docker_push("reddit-app", "latest", "anurag904")
                echo "Image Push Sucessful.."
            }
        }
        stage("Code Testing"){
            steps{
                echo "Code Testing Started.."
            }
        }
        stage("Code Deploy"){
            steps{
                echo "Deployment Started."
                sh "docker-compose down"
                sh "docker-compose up -d"
                echo "Deployment Successful."
            }
        }
    }
}
