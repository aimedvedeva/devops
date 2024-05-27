pipeline {
    agent any

    tools {
        go 'go-1.22'
    }

    stages {
        stage('Build') {
            steps {
                sh 'go build main.go'
                sh 'ls -la'
                sh 'echo "Build done!!!"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo Deploying...'
                withCredentials([sshUserPrivateKey(credentialsId: 'mykey', keyFileVariable: 'mykey')]) {
                    sh 'ls -la'
                    sh "scp -o StrictHostKeychecking=no -i ${mykey} main vagrant@192.168.105.3:"
                }
            }
        }
    }
}
