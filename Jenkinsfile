pipeline {
    agent any
    tools {
        jdk 'JDK22'
        maven 'Maven3'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build & Test with Coverage') {
            steps {
                sh 'mvn clean test'
            }
        }
    }
    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts artifacts: 'target/site/jacoco/**', fingerprint: true
        }
    }
}
