pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the repository
                git 'https://github.com/your-username/calculator-app.git'
            }
        }

        stage('Build') {
            steps {
                // Build the project using Maven
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                // Run tests using Maven
                sh 'mvn test'
            }
        }

        stage('Code Coverage') {
            steps {
                // Generate code coverage report using Jacoco
                sh 'mvn jacoco:report'
                // Publish the code coverage report in Jenkins
                jacoco(execPattern: '**/target/site/jacoco/*.xml')
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the application to a server or container
                sh 'docker build -t calculator-app .'
                sh 'docker run -p 8080:8080 calculator-app'
            }
        }
    }
}

