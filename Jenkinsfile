pipeline {
    agent any

    environment {
        PROJECT_NAME = 'jenkins-learning'
        BUILD_ENV = 'sandbox'
    }

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

    stages {
        stage('Print Environment') {
            steps {
                echo "Project: ${PROJECT_NAME}"
                echo "Environment: ${BUILD_ENV}"

                sh 'env | sort'
            }
        }
    }
}