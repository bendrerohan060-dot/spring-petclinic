pipeline {
    agent any

    tools {
        maven 'Maven 3.9'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                dir('spring-petclinic-main') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage('Unit Test') {
            steps {
                dir('spring-petclinic-main') {
                    sh 'mvn test'
                }
            }
            post {
                always {
                    junit 'spring-petclinic-main/target/surefire-reports/*.xml'
                }
            }
        }
    }
}
