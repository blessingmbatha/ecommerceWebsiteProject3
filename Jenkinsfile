pipeline {
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven3'
    }

    stages {
        stage('Cleanup Workspace') {
            steps {
                CleanWs ()
            }
        }
        
        stage('Git Checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/blessingmbatha/ecommerceWebsiteProject3.git'
            }
        }

        stage('Code Compile') {
            steps {
                sh "mvn clean compile"
            }
        }

        stage('Run Code Test') {
            steps {
                sh "mvn test"
            }
        }
    }
}
