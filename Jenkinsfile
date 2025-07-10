pipeline {
    agent any

    tools {
        maven 'Maven 3.9.10'
        jdk 'JDK 17'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ashiq506/selenium-testng-project-with-jenkins.git'
            }
        }

        stage('Build and Test') {
            steps {
                bat 'mvn clean test' // use `sh` instead of `bat` if on Linux
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
            archiveArtifacts artifacts: 'reports/*.html', allowEmptyArchive: true
        }
    }
}
