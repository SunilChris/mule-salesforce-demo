pipeline {
    agent any
    environment {
        ANYPOINT_USER = credentials('anypoint-username').username
        ANYPOINT_PASS = credentials('anypoint-password').password
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/SunilChris/mule-salesforce-demo.git'
            }
        }
        stage('Build & Deploy') {
            steps {
                sh 'mvn clean package'
                sh 'mvn deploy -Danypoint.username=$ANYPOINT_USER -Danypoint.password=$ANYPOINT_PASS'
            }
        }
    }
    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Deployment Failed!'
        }
    }
}