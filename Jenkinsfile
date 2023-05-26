pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t example2 .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run -p 5000:5000 -d example2'
                sleep 10
                sh 'curl http://10.142.0.6:5000'
                sh 'docker kill $(docker ps -q)'
            }
        }

        stage('Deploy') {
            steps {
                // Replace with your deployment steps
                sh 'docker push example2:latest'
                // Additional steps for deployment
            }
        }
    }
}
