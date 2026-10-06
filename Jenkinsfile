
pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
        jdk 'java'
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
}
