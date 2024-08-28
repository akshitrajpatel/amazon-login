pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9' // Replace with your Jenkins Maven installation name
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the linked GitHub repository
                git url: 'https://github.com/akshitrajpatel/amazon-jenkins-login.git' // Replace with your GitHub repository URL
            }
        }

        stage('Build') {
            steps {
                // Clean and build the Maven project
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Execute the test cases
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            // Archive the test results
            junit '**/target/surefire-reports/*.xml'
        }
        failure {
            // Notify on failure
            echo 'Build failed!'
        }
    }
}
