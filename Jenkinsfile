pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Specify build tool (e.g., Maven)
                // sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Specify test automation tools (e.g., JUnit, TestNG)
                // sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
                // Specify code analysis tool (e.g., SonarQube)
                // sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Specify security scan tool (e.g., OWASP Dependency-Check)
                // sh 'dependency-check --scan .'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
                // Deploy to staging (e.g., using SCP, AWS CLI)
                // sh 'scp target/*.jar user@staging-server:/path/to/deploy'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Run integration tests (e.g., using Selenium)
                // sh 'mvn verify -Pstaging'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server...'
                // Deploy to production (e.g., using SCP, AWS CLI)
                // sh 'scp target/*.jar user@production-server:/path/to/deploy'
            }
        }
    }
    post {
        success {
        mail to: 'lahiruvimukthi292@gmail.com',
             subject: "SUCCESS: ${env.JOB_NAME} (${env.BUILD_NUMBER})",
             body: "The build was successful.\n\nLogs:\n${env.BUILD_URL}consoleText"
        }
        failure {
        mail to: 'lahiruvimukthi292@gmail.com',
             subject: "FAILURE: ${env.JOB_NAME} (${env.BUILD_NUMBER})",
             body: "The build failed.\n\nLogs:\n${env.BUILD_URL}consoleText"
        }
    }
}
