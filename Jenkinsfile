pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Your build commands go here
                    sh 'mvn clean install'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Your deployment commands go here
                    sh 'scp target/myapp.war user@remote-server:/path/to/deployment/directory'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }

        failure {
            echo 'Build or deployment failed!'
        }
    }
}
