pipeline {
    agent any

    stages {
        stage('Dockerize') {
            steps {
                sh 'docker build -t ttl.sh/myapp .'
                sh 'docker images'
                }
            }
        stage ('Push image') {
            steps {
                sh 'docker push ttl.sh/myapp'
            }
        }
        stage ('Pull image on target') {
            steps {
                sh 'echo Deploying...'
                withCredentials([sshUserPrivateKey(credentialsId: 'mykey', keyFileVariable: 'mykey')]) {
                    sh 'ls -la'
                    sh "ssh -o StrictHostKeychecking=no -i ${mykey} vagrant@192.168.105.3: 'docker pull ttl.sh/myapp'"
                }
            }
        }
    }
}
