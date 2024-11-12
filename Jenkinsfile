@Library('Shared')_

pipeline{
    agent {label 'dev-server'}
    
    stages{
        stage("Code"){
            steps{
                clone("https://github.com/Amitabh-DevOps/Project-04-Django-notes-app-declarative-cidd.git","dev")
                // git url: "https://github.com/Amitabh-DevOps/Project-04-Django-notes-app-declarative-cidd.git" , branch: "dev"
                echo "Code clonning done."
            }
        }
        stage("Build"){                                                             
            steps{
                dockerbuild("django-notes-app","latest")
                // sh "docker build -t notes-app ."
                echo "Code build bhi hogaya."
            }
        }
        stage("Push to DockerHub"){
            steps{
                // withCredentials([usernamePassword (credentialsId: "dockerHub", passwordVariable: "dockerHubPass", usernameVariable: "dockerHubUser")])
                // {
                //     sh "docker image tag notes-app ${env.dockerHubUser}/django-notes-app:latest"
                //     sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                //     sh "docker push ${env.dockerHubUser}/django-notes-app:latest"
                // }
                dockerpush("dockerHub","django-notes-app","latest")
                echo "Push to dockerHub is also done."
            }
        }
        stage("Deplying"){
            steps{
                deploy()
                // sh "docker compose down && docker compose up -d --build"
                echo "Deployment bhi done."
            }
        }
    }
}
