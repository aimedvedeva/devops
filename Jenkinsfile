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
        stage('Deploy to preprod') {
            environment {
                ANSIBLE_HOST_KEY_CHECKING = 'false'
            }
            steps {
                sh 'echo Deploying...'
                ansiblePlaybook credentialsId: 'mykey', inventory: 'hosts.ini', playbook: 'playbook.yml'
            }
        }
        stage('Deploy to staging') {
            environment {
                ANSIBLE_HOST_KEY_CHECKING = 'false'
            }
            steps {
                sh 'echo Deploying...'
                ansiblePlaybook credentialsId: 'mykey', inventory: 'target.ini', playbook: 'playbook.yml'
            }
        }

    }
}
