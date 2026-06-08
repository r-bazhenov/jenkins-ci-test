pipeline {
    agent any

    stages {

        stage('Environment') {
            steps {
                sh 'pwd'
                sh 'ls -la'
                sh 'java -version'
            }
        }

        stage('Build') {
            steps {
                sh 'chmod +x gradlew'
                sh './gradlew clean build'
            }
        }

        stage('Artifacts') {
            steps {
                sh 'ls -la build/libs'
            }
        }
    }
}