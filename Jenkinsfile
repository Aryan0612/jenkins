pipeline {
    agent {label 'master-node1'} // Runs on any available agent
    
    tools {
        maven 'maven 3.9' // Use configured Maven tool
    }

    environment {
        MVN_CMD = "mvn clean install" // Define Maven command
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository for a specific branch
                git branch: 'master', url: 'https://github.com/jenkins-docs/simple-java-maven-app.git'
            }
        }

        stage('Build') {
            steps {
                // Run Maven build
                 mvn 'clean install'
            }
        }

        stage('Test') {
            steps {
                // Run Maven tests
                mvn 'test'
            }
        }

        stage('Deploy') {
            steps {
                // Run deployment (customize with your deployment steps)
                echo 'Deploying the project...'
                script {
                    def numbers = [5, 3, 8, 1, 2]
                    numbers.sort()
                    echo "Sorted numbers: ${numbers}"
                }
            }
        }
    }

    post {
        always {
            // This will run after the pipeline finishes, regardless of success or failure
            echo 'Cleaning up...'
        }
        success {
            echo 'Build and tests completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
