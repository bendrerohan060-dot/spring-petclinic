pipeline {
    agent any

    tools {
        maven 'Maven 3.9'
        jdk 'JDK 21'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Spring PetClinic project'
                dir('spring-petclinic-main') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage('Unit Test') {
            steps {
                echo 'Running JUnit tests'
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

    post {
        success {
            echo 'Java CI Pipeline completed successfully'
        }
        failure {
            echo 'Java CI Pipeline failed'
        }
    }
}
