pipeline {
    agent any
    stages {
        stage('code'){
            steps {
                git url: 'https://github.com/Kaneryaa/node-todo-cicd.git', branch: 'master' 
               
            }
        }
        stage('build'){
            steps {
              echo 'echo "Building"'
              sh " docker build . -t danish1234512/nodejs-jenkins:latest"
            }
        }
        stage('push'){
            steps {
              withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]){
               sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}" 
               sh " docker push danish1234512/nodejs-jenkins:latest"
              }
            }
        }
        
        stage('Test') {
            steps {
                // sh 'npm install'
                // sh 'npm test'
                echo "test"
            }
        }
        stage('deploy'){
            steps {
             sh "docker-compose up"
            }
        }
    }
}
