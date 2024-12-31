pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M398"
    }

    stages {
        stage('Echo Version') {
            steps {
                sh 'echo Print mn Version'
                sh 'mvn -version'
            }
        }
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/Muhamed404/jenkins-hello-world.git'
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage('Unit Test') {
            steps {
                sh 'mvn test'
            }
            
        }

    }
}
