pipeline {
    agent any

    tools {
        // Install the Java version specified in your environment or Jenkins config
        jdk 'JDK11'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                git url: 'https://github.com/pranjalmaheshwarii/hello__world.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                // Compile the Java program
                sh 'javac HelloWorld.java'
            }
        }

        stage('Run') {
            steps {
                // Run the Java program
                sh 'java HelloWorld'
            }
        }
    }

    post {
        success {
            echo 'Hello World program ran successfully.'
        }
        failure {
            echo 'There was a problem running the Hello World program.'
        }
    }
}

