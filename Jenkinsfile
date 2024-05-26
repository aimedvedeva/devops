pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'go build main.go'
                sh 'ls -la'
                sh 'echo "Build done!!!"'
            }
        }
    }
}
