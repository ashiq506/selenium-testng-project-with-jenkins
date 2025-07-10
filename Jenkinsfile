pipeline {
    agent any

    tools {
        maven 'Maven 3.8.10' // Must be configured in Jenkins (Manage Jenkins → Global Tool Configuration)
        jdk 'JDK 11'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ashiq506/selenium-testng-project-with-jenkins.git'
            }
        }

        stage('Build and Test') {
            steps {
                bat 'mvn clean test'
            }
        }
    }

    post {
        always {
            // Publish JUnit test results
            junit 'target/surefire-reports/*.xml'

            // Archive HTML ExtentReport
            archiveArtifacts artifacts: 'reports/*.html', allowEmptyArchive: true
        }
    }
}
