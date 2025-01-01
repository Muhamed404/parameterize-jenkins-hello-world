pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M398" and add it to the path.
        maven "M398"
    }

    stages {
    
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
        stage('Containerization') {
            steps{
                sh 'echo Docker Build Image.......... '
                sh 'echo Docker Tag Image............'
                sh 'echo Docker push Image...........'
            }
        }

        stage('Kubernetes Deployment') {
            steps{
                sh 'echo Deploy to kubernetes Using ArgoCD'
            }
        } 
        stage('Integration Testing'){
            steps{
                sh "sleep ${params.SLEEP_TIME}"
                sh "echo ............Testing Done Via URL................" 
            }
        }
        
    }
}
