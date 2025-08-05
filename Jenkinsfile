pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker Image...'
                sh 'docker build -t jenkins-nodejs-demo .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing... (this is a dummy test)'
                sh 'echo "Test Passed!"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Running Container...'
                // Stop old container if exists
                sh '''
                    docker ps -q --filter "name=jenkins-nodejs-demo" | grep -q . && docker stop jenkins-nodejs-demo && docker rm jenkins-nodejs-demo || true
                    docker run -d --name jenkins-nodejs-demo -p 3000:3000 jenkins-nodejs-demo
                '''
            }
        }
    }
}
// # testing for auto trigerring 