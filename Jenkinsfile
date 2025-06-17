pipeline {
    agent any

    parameters {
        string(name: 'USERNAME', defaultValue: 'guest', description: 'Enter your username')
        choice(name: 'ENV', choices: ['dev', 'staging', 'prod'], description: 'Choose the deployment environment')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run tests before deploy?')
    }

    stages {
        stage('Print Parameters') {
            steps {
                echo "Username: ${params.USERNAME}"
                echo "Environment: ${params.ENV}"
                echo "Run Tests: ${params.RUN_TESTS}"
            }
        }

        stage('Conditional Test') {
            when {
                expression { return params.RUN_TESTS == true }
            }
            steps {
                echo "Running tests for ${params.ENV}..."
                // You can add actual test commands here
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENV} as ${params.USERNAME}..."
                // Add your deploy script here
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
