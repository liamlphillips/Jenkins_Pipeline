pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build using Maven'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Run tests using JUnit'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyse code using SonarQube'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Scan using OWASP ZAP'
            }

            post {
                success {
                    emailext(
                        to: 'liam.lphillips@gmail.com',
                        subject: 'Security scan complete',
                        body: 'The security scan completed successfully. Check the attached logs.',
                        attachLog: true
                    )
                }

                failure {
                    emailext(
                        to: 'liam.lphillips@gmail.com',
                        subject: 'Security scan failed',
                        body: 'The security scan failed. Check the attached logs.',
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploy to AWS EC2 staging server'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Run integration tests on staging'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploy to production server'
            }
        }
    }
}
