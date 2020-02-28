pipeline {
    agent {
        label 'docker-in-docker'
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn compile' 
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh 'mvn package'
            }
        }
    }
}
