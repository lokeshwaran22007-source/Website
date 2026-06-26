pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t website .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop website || true
                docker rm website || true
                docker run -d -p 8081:80 --name website website
                '''
            }
        }
    }
}
