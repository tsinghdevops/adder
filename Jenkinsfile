pipeline {
    agent any

    stages {
        /*stage('Checkout') {
            steps {
                // Checkout the code from version control
                checkout scm
            }
        }*/

        stage('Build') {
            steps {
                // Build the project using Maven
                script {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                // Run unit tests using Maven
                script {
                    sh 'mvn test'
                }
            }
            post {
                always {
                    // Archive test results
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the application
                // This step will vary based on your deployment strategy
                script {
                    sh 'mvn deploy'
                }
            }
        }
    }

    post {
        always {
            // Cleanup or notifications
            echo 'Cleaning up...'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }