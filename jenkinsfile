pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t website .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                sudo docker stop website || true
                sudo docker rm website || true
                sudo docker run -d -p 8081:80 --name website website
                '''
            }
        }
    }
}
