pipeline {
    agent any

    tools {
        maven 'myMaven' // Ensure this version is configured in Jenkins
        jdk 'myJDK'      // Ensure this JDK version is configured in Jenkins
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from SCM
                git 'https://github.com/atulkamble/maven-project.git:main'
                sh 'java --version'
            }
        }

        stage('Build') {
            steps {
                // Build the project using Maven
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run unit tests
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                // Package the application
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                // Simple deployment example
                sh 'echo "Deploying application..."'
                // Example of copying artifacts to a deploy location
                sh 'cp target/myproject-1.0.jar /target/*.jar'
            }
        }
    }

    post {
        always {
            // Clean up actions
            sh 'echo "Cleaning up..."'
        }

        success {
            // Actions on successful build
            echo 'Build succeeded!'
        }

        failure {
            // Actions on failed build
            echo 'Build failed!'
        }
    }
}