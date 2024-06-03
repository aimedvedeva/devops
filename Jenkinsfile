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
               withCredentials([file(credentialsId:'kubernetis-config', variable:'kubeconfig')]){
                   sh 'cp $kubeconfig ~/.kube/config'
                   sh 'kubectl apply -f deployment.yaml --validate=false'
'
               }
           }
       }
    }
}
