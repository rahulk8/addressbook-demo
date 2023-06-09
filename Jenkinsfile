pipeline {
    agent any
    tools{
        maven 'my_maven'
    }
    stages {
        stage('Code checkout') {
            steps {
                git 'https://github.com/rahulk8/addressbook-demo.git'
            }
        }
        stage('Build the Sourcecode') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy the same to a tocat server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: 'http://13.127.50.222:8081/')], contextPath: 'addressbookdl', war: '**/*.war'
            }
        }
    }
}
