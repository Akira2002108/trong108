pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'dockerhub-credentials'
        EMAIL_CREDENTIALS_ID = 'gmail-credentials'
        DOCKERHUB_REPO = 'vanle96/halloween-respons'
        BRANCH_NAME = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/VanLeDinh96/nodejs-reactjs.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    docker.build("${DOCKERHUB_REPO}:0.0.1")
                }
            }
        }

        // stage('Push') {
        //     steps {
        //         script {
        //             docker.withRegistry('', "${DOCKER_CREDENTIALS_ID}") {
        //                 docker.image("${DOCKERHUB_REPO}:latest").push()
        //             }
        //         }
        //     }
        // }

        // stage('Deploy') {
        //     steps {
        //         sh 'docker-compose down'
        //         sh 'docker-compose up -d'
        //     }
        // }

        // stage('Notify') {
        //     steps {
        //         emailext (
        //             subject: "Build ${currentBuild.fullDisplayName} - ${currentBuild.currentResult}",
        //             body: "Build ${currentBuild.fullDisplayName} finished with status: ${currentBuild.currentResult}. Check console output at ${env.BUILD_URL} to view the results.",
        //             recipientProviders: [[$class: 'DevelopersRecipientProvider']],
        //             from: 'dinhvanle.it@gmail.com',
        //             to: 'yamatole312@gmail.com'
        //         )
        //     }
        // }
    }

    post {
        always {
            cleanWs()
        }
    }
}