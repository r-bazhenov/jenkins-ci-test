def printBuildInfo(fio) {
    echo "Build: ${env.BUILD_NUMBER} : ${fio}"
    echo "Job: ${env.JOB_NAME} : ${fio}"
}

pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'test', 'prod'],
            description: ''
        )
    }

    stages {
        stage('Decision') {
            steps {
                script {
                    echo "Selected: ${params.ENVIRONMENT}"

                    if (params.ENVIRONMENT == 'prod') {
                        echo 'Production deployment'
                    } else {
                        echo 'Non-production deployment'
                    }

                    def config = [
                        env: 'dev',
                        replicas: 2,
                        namespace: 'sandbox'
                    ]

                    echo config.env
                    echo config.namespace

                    def services = [
                        'user-service',
                        'order-service',
                        'payment-service'
                    ]

                    for (service in services) {
                        echo service
                    }

                    printBuildInfo('rbs')
                }
            }
        }
    }
}