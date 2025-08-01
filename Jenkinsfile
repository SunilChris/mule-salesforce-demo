pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/SunilChris/mule-salesforce-demo.git'
            }
        }
        stage('Build & Deploy') {
            steps {
                sh 'mvn clean package'
                sh 'mvn deploy -Danypoint.username=$ANYPOINT_USER -Danypoint.password=$ANYPOINT_PASS'
            }
        }
    }
}