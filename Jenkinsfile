pipeline{
    agent {
        docker {
            image 'node:18.17.1-alpine3.18'
        }
    }
    environment {
    FIREBASE_DEPLOY_TOKEN = credentials('firebase-token')
    }

 stages{
        stage('Building'){
            steps{
            sh 'npm install -g firebase-tools'
            }
        } 
        stage('Testing'){
            steps{
            sh 'firebase deploy -P devops-proj-testing --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        } 
        stage('Staging'){
            steps{
            echo 'This is Testing.'
            }
        } 
        stage('Production'){
            steps{
            echo 'This is Testing.'
            }
        } 
    }

}