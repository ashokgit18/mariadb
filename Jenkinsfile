pipeline {
    agent any
    options { buildDiscarder(logRotator(numToKeepStr: '10')) }
    
    stages {
        stage('helm version') {
            steps {
                sh 'helm version'
            }
        }
    stage('deploy mariadb') {
            steps {
               sh '''cd $WORKSPACE
                   helm upgrade --install devops18-mariadb maridb --namespace $WORKSPACE/mariadb --values $WORKSPACE/mariadb/createat-mariadb.yaml'''
            }
        }
    stage('verification') {
            steps {
                sh 'kubectl get po -n mariadb '
            }
        }
    
    }
}
