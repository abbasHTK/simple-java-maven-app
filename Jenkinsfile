pipeline {
    agent {
        docker {
            // execute the pipeline on a Docker image
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                // execute the maven build command
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deliver') { 
            steps {
                // execute a deploy script under project root /jenkins/...
                sh './jenkins/scripts/deliver.sh' 
            }
        }
    }
}
