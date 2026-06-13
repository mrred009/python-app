pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'python3 app.py'
            }
        }

        stage('Test') {
            steps {
                sh 'python3 -m pip install pytest --break-system-packages'
                sh 'python3 -m pytest'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t python-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker save python-app > app.tar

                scp -o StrictHostKeyChecking=no app.tar ubuntu@172.31.43.191:/home/ubuntu/

                ssh -o StrictHostKeyChecking=no ubuntu@172.31.43.191 "
                    docker load < app.tar
                    docker stop python-app || true
                    docker rm python-app || true
                    docker run -d --name python-app python-app
                "
                '''
            }
        }
    }
}
