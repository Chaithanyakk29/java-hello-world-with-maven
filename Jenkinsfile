
pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }
    
    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Welcome') {
            steps {
                echo 'Welcome! Jenkins pipeline is working.'
            }
        }

        stage('Clean') {
            steps {
                bat 'mvn -B clean'
            }
        }

        stage('Compile') {
            steps {
                bat 'mvn -B compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn -B test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn -B package -DskipTests'
            }
        }
    }
    
    post {
        success {
            emailext(
                to: 'YOUR_GMAIL@gmail.com',
                subject: "Jenkins SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build #${env.BUILD_NUMBER} completed successfully. Check Jenkins for details."
            )
        }

        failure {
            emailext(
                to: 'YOUR_GMAIL@gmail.com',
                subject: "Jenkins FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build #${env.BUILD_NUMBER} failed. Please check the Jenkins console output."
            )
        }
    }

}
