pipeline {
    agent any
    stages {
        stage('Starting'){
            steps {
                sh 'echo "Starting the process"'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
        stage('Closing'){
            steps {
                sh 'echo "Closing the process"'
            }
        }
    }
}
