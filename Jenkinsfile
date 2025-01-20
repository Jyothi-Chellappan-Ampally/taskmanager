pipeline {
    agent { label 'dev-agent' }
    
    stages{
        stage('Code'){
            steps {
                git url: 'https://github.com/Jyothi-Chellappan-Ampally/node-todo-cicd-master.git', branch: 'master'
            }
        }
        stage('Build and Test'){
            steps {
                sh 'docker build . -t Jyothi-Chellappan-Ampally/node-todo-app-cicd:latest' 
            }
        }
        // stage('Login and Push Image'){
        //     steps {
        //         echo 'logging in to docker hub and pushing image..'
        //         withCredentials([usernamePassword(credentialsId:'dockerHub',passwordVariable:'', usernameVariable:'jyothichellappanampally')]) {
        //             sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
        //             sh "docker push Jyothi-Chellappan-Ampally/node-todo-app-cicd:latest"
        //         }
        //     }
        // }
        stage('Deploy'){
            steps {
                sh 'docker-compose down && docker-compose up -d'
            }
        }
        stage('run'){
            steps{
                sh 'docker pull node-todo-app-cicd:latest'
            }
        }
    }
}
