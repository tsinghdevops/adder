pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Build the project using Maven
                script {
                    sh 'mvn clean install'
                }
            }
        }
    }
}