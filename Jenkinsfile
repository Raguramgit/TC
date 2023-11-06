pipeline {
    agent any
    tools{
        jdk 'jdk11'
        maven 'maven3'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Raguramgit/TC.git'
            }
        }
        stage('Code Compile') {
            steps {
                sh "mvn compile"
            }
        }
        stage('Test Cases') {
            steps {
                sh "mvn test"
            }
        }
        stage('Code Build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('Deploy To Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://54.179.225.236:8082/')], contextPath: 'planview', onFailure: false, war: 'target/*.war'
            }
        }
        
    }
}
