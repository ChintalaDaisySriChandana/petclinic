@Library('my-shared-library') _  // Import shared library

pipeline {
    agent any

    environment {
        GIT_CREDENTIALS = credentials('git-credentials-id')  // Define Git credentials ID for SCM
    }

    stages {
        stage('Checkout SCM') {
            steps {
                script {
                    // Checkout code from the repository (using Jenkins SCM configuration)
                    checkout scm
                    // Or specify the git checkout directly if required
                    // git url: 'https://github.com/ChintalaDaisySriChandana/petclinic.git', branch: 'main', credentialsId: 'git-credentials-id'
                }
            }
        }

        stage('Setup Java') {
            steps {
                script {
                    // Setup Java (could be an install or configuration task)
                    sh 'java -version'
                }
            }
        }

        stage('Setup Maven') {
            steps {
                script {
                    // Setup Maven (e.g., check Maven version)
                    sh 'mvn -v'
                }
            }
        }

        stage('Build and Test') {
            steps {
                script {
                    // Execute Maven build and tests
                    sh 'mvn clean install'
                }
            }
        }

        stage('Upload Artifact') {
            steps {
                script {
                    // Upload build artifacts (optional)
                    echo "Uploading artifacts..."
                }
            }
        }

        stage('Run Application') {
            steps {
                script {
                    // Run the application (e.g., starting a service or application)
                    echo "Running the application..."
                }
            }
        }

        stage('Validate Application') {
            steps {
                script {
                    // Validate if the application is running as expected (health check, etc.)
                    echo "Validating the application..."
                }
            }
        }

        stage('Stop Spring') {
            steps {
                script {
                    // Stop Spring or any running services
                    echo "Stopping Spring Application..."
                }
            }
        }
    }

    post {
        always {
            script {
                // Run cleanup tasks after the pipeline, whether successful or failed
                echo "Cleaning up..."
                // Example: call shared cleanup function
                // cleanupProcesses()  // Ensure this is defined in your shared library
            }
        }
        success {
            echo "Pipeline executed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
