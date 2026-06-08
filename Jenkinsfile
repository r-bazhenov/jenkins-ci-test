pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'test', 'prod'],
            description: 'Target environment'
        )
    }

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
        stage('Print Environment') {
            steps {
                echo "Project: ${PROJECT_NAME}"
                echo "Environment: ${BUILD_ENV}"

                sh 'env | sort'
            }
        }
        stage('Show Parameters') {
            steps {
                echo "Branch: ${params.BRANCH_NAME}"
            }
        }
    }
}