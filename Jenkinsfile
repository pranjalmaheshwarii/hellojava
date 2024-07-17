pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'tomcat'
        DOCKER_CONTAINER = 'tomcat-server'
        DOCKER_PORT = '8090'
        GITHUB_REPO = 'https://github.com/pranjalmaheshwarii/hellojava.git'
        JAVA_FILE = 'HelloWorld.java'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: "https://github.com/pranjalmaheshwarii/hellojava.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                sh 'javac HelloWorld.java'
            }
        }
        stage('Package') {
            steps {
                sh '''
                mkdir -p webapps/ROOT/WEB-INF/classes
                cp HelloWorld.class webapps/ROOT/WEB-INF/classes
                '''
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def containerExists = sh(script: "docker ps -q -f name tomcat-server", returnStatus: true) == 0
                    if (containerExists) {
                        sh "docker cp webapps tomcat-serever:/usr/local/tomcat/webapps"
                    } else {
                        sh "docker run -d -p 34.16.164.80:8080 -v $(pwd)/webapps:/usr/local/tomcat/webapps --name tomcat-server tomcat"
                    }
                }
            }
        
    }
    post {
        always {
            cleanWs()
        }
    }
}
