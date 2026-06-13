stage('Test') {
    steps {
        sh 'python3 -m pip install pytest'
        sh 'pytest'
    }
}
stage('Test') {
    steps {
        sh 'python3 -m pip install pytest --break-system-packages'
        sh 'pytest'
    }
}
