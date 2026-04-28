pipeline {
    agent any

    tools {
        jdk 'Java_JDK'
        maven 'MAVEN'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/nextgentestingacademy/ITV-Maven-Batch703.git',
                    branch: 'main'
            }
        }

        stage('Build & Test') {
            steps {
                bat "mvn clean test"
            }
        }
    }
}