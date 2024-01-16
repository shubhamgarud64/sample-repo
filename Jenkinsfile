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

        stage('Parallel Tests') {
            parallel {
                stage('Unit Tests') {
                    steps {
                        script {
                            // Run unit tests
                            sh 'mvn test'
                        }
                    }
                }

                stage('Integration Tests') {
                    steps {
                        script {
                            // Run integration tests
                            sh 'mvn integration-test'
                        }
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Testing completed!'
        }
    }
}
