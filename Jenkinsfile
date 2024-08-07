pipeline {
    agent any
    stages{
        stage('Clone') {
            steps {
                    git branch: 'main', credentialsId: 'github', url: 'https://github.com/Akira2002108/trong108.git'        
                    }
        }
        stage('Push Docker Hub') {
            steps {
                withDockerRegistry(credentialsId: 'dockerhub', url:'') 
                {
                    sh label: '', script: 'docker build -t nguyenhuutrong/huutrong .'
                    sh label: '', script: 'docker push nguyenhuutrong/huutrong'
                }
            }
        }
    }
    post {
        always {
            mail bcc: '', body: '1234', cc: '', from: '', replyTo: '', subject: 'trong send', to: 'taitinhno3@gmail.com'
        }
    }
}