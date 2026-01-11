pipeline {
    agent {
        docker {
            image 'maven:3.9.9-eclipse-temurin-17'
            args '-v /root/.m2:/root/.m2'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/derrazmed/Mini-Projet-DevOps-DerrazElKabirMohamed.git'
            }
        }

        stage('Build & Test') {
            steps {
                dir('demo') {
                    sh 'mvn clean test package'
                }
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'demo/target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
            }
        }
    }

    post {
        success {
            echo 'Pipeline SUCCESS'
        }
        failure {
            echo 'Pipeline FAILED'
        }
    }
}
