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
        stage('Testing Environment'){
            steps{
            sh 'firebase deploy -P devops-proj-testing --token "$FIREBASE_DEPLOY_TOKEN"'
            input message: 'After testing. Do you want to continue with Staging Environment? (Click "Proceed" to continue)'
            }
        } 
        stage('Staging Environment'){
            steps{
             sh 'firebase deploy -P devops-proj-staging --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        } 
        stage('Production Environment'){
            steps{
            sh 'firebase deploy -P devops-proj-production-bcfd9 --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        } 
    }

}