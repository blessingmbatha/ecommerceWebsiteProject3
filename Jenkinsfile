pipeline {
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven3'
    }

    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs ()
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
        stage('Sonarqube Analysis') {
        steps {
             withSonarQubeEnv('sonar-sever') {
             withMaven(maven:'maven3') {
             sh 'mvn clean package sonar:sonar'
                 }
             }
          }
       }
    }
}
