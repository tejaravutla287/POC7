pipeline {
    agent any
 
    environment {
        DOCKER_IMAGE = "my-poc-app"
        DOCKER_TAG = "${env.BUILD_NUMBER}"
    }
 
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/tejaravutla287/POC7.git'
            }
        }
 
        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} ."
                }
            }
        }
 
        stage('Deploy with Ansible') {
            steps {
                // This assumes your playbook is in the repo root
                // Note: Ensure the 'jenkins' user has ssh access to the target
                sh "ansible-playbook -i localhost, deploy.yml"
            }
        }
    }
}
