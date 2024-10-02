#!/usr/bin.env groovy

pipeline {
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    echo "Testing the application..."

                }
            }
        }
        stage("build") {
            steps {
                script {
                    echo "Building the application..."
                }
            }
        }

        stage("deploy") {
            steps {
                script {
                    def dockerCmd = 'docker run -p 3000:3080 -d ebony9ja/aws-docker:1.0'
                    sshagent(['ec2-user-key']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@18.184.54.160 ${dockerCmd}"
                    }
                }
            }
        }
    }
} 
