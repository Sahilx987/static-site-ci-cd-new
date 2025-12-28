pipeline {
    agent any

    stages {
        stage('Build Image') {
            steps {
                sh 'docker build -t real-site .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                  docker rm -f real-site || true
                  docker run -d -p 8082:80 --name real-site real-site
                '''
            }
        }

        stage('Verify') {
            steps {
                sh 'curl http://localhost:8082'
            }
        }
    }
}

