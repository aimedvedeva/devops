pipeline {
    agent any

    stages {
        stage('Dockerize') {
            steps {
                sh 'docker build -t ttl.sh/myapp1 .'
                sh 'docker images'
                }
            }
        stage ('Push image') {
            steps {
                sh 'docker push ttl.sh/myapp1'
            }
        }
       stage ('Deploy') {
           steps {
               sh 'kubectl apply -f deployment.yaml'
           }
       }
    }
}
