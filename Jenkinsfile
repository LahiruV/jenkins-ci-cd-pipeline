pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Using Maven as a build tool
                sh 'mvn clean package'
                // Alternative: Using Gradle
                // sh 'gradle build'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Using JUnit for unit tests
                sh 'mvn test'
                // Alternative: Using Mocha for JavaScript projects
                // sh 'npm test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
                // Using SonarQube for code analysis
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
                // Alternative: Using ESLint for JavaScript
                // sh 'eslint .'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Using OWASP Dependency-Check for security scanning
                sh 'dependency-check --project my-app --scan . --format XML --out dependency-check-report.xml'
                // Alternative: Using Bandit for Python code
                // sh 'bandit -r .'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
                // Deploy to staging using SCP
                sh 'scp target/*.jar user@staging-server:/path/to/deploy'
                // Alternative: Using Docker for containerized deployment
                // sh 'docker build -t myapp . && docker run -d -p 8080:8080 myapp'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Using Maven to run integration tests on staging
                sh 'mvn verify -Pstaging'
                // Alternative: Using Postman/Newman for API testing
                // sh 'newman run my_collection.json'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server...'
                // Deploy to production using SCP
                sh 'scp target/*.jar user@production-server:/path/to/deploy'
                // Alternative: Using Kubernetes for orchestrated deployment
                // sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
    post {
        success {
            // Send email notification on success
            mail to: 'lahiruvimukthi292@gmail.com',
                 subject: "SUCCESS: ${env.JOB_NAME} (${env.BUILD_NUMBER})",
                 body: "The build was successful.\n\nLogs:\n${env.BUILD_URL}consoleText"
            
            // Send Slack notification on success
            slackSend(channel: '#build-status', message: "SUCCESS: ${env.JOB_NAME} (${env.BUILD_NUMBER})")
        }
        failure {
            // Send email notification on failure
            mail to: 'lahiruvimukthi292@gmail.com',
                 subject: "FAILURE: ${env.JOB_NAME} (${env.BUILD_NUMBER})",
                 body: "The build failed.\n\nLogs:\n${env.BUILD_URL}consoleText"
            
            // Send Slack notification on failure
            slackSend(channel: '#build-status', message: "FAILURE: ${env.JOB_NAME} (${env.BUILD_NUMBER})")
        }
    }
}
