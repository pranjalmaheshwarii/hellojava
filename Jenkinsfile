pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/pranjalmaheshwarii/hellojava.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'javac HelloWorld.java'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'cp HelloWorld.class /opt/tomcat/webapps/ROOT/'
                sh '/opt/tomcat/bin/shutdown.sh'
                sh '/opt/tomcat/bin/startup.sh'
            }
        }
    }
}
