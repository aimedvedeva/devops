pipeline {
    agent any

    stages {
        stage('Dockerize') {
            steps {
                // sh 'echo Deploying...'
                // withCredentials([sshUserPrivateKey(credentialsId: 'mykey', keyFileVariable: 'mykey')]) {
                //     sh 'ls -la'
                //     sh "scp -o StrictHostKeychecking=no -i ${mykey} main vagrant@192.168.105.3:"
                sh 'docker build -t myapp'
                sh 'docker images'
                }
            }
        }
}
