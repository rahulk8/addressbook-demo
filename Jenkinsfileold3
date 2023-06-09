pipeline {
    agent any
    tools{
        maven 'my_maven'
    }
    stages {
        stage('Code checkout') {
            steps {
                git 'https://github.com/niladrimondal/addressbook-demo.git'
            }
        }
        stage('Build the Sourcecode') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy the same to a tocat server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: 'http://54.183.235.158:8081/')], contextPath: 'addressbooksc', war: '**/*.war'
            }
        }
    }
}
