pipeline {
    agent any
    
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    git branch: 'master', url: 'https://github.com/loki-4321/maven.git'
                }
            }
        }
        
        stage('Maven build') {
            steps {
                script {
                    sh 'mvn clean package install'
                }
            }
        }
        
        stage('Static code analysis') {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'cred') {
                        sh 'mvn sonar:sonar'
                    }
                }
            }
        }
        
    }
}
