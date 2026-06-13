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
                sh 'python3 -m pytest''
            }
        }
    }
}

