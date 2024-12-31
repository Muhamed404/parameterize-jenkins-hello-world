pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M398"
    }

    stages {
        stage('Maven Version') {
            steps {
                sh 'echo Print Mavnen Version'
                sh 'mvn -version'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests=true'
                archiveArtifacts 'target/hello-demo-*.jar'
            }
        }
        stage('Unit Test') {
            steps {
                sh 'mvn test'
                junit(testResults: 'target/surefire-reports/TEST-*.xml', keepProperties: true, keepTestNames: true)
            }
            
        }
        stage('Local Deployment') {
            steps {
                sh """ java -jar target/hello-demo-*.jar > /dev/null & """
            }
        }
        stage('Integration Testing'){
            steps{
                sh 'sleep 5s'
                sh 'curl -s http://localhost:6767/hello'
            }
        }

    }
}
