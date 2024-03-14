pipeline {
    agent none

    stages {
        stage('Build Docker Image with DinD') {
            agent {
                kubernetes {
                    defaultContainer 'dind'
                    yamlFile 'dind.yaml'
                }
            }

            environment {
                ACR_CREDS = credentials('acr-sp')
            }

            steps {
                sh 'docker login --username $ACR_CREDS_USR --password $ACR_CREDS_PSW'
                sh 'docker build -t thachthucregistry.azurecr.io/minimal-java:latest .'
                sh 'docker push thachthucregistry.azurecr.io/minimal-java:latest'
            }
        }
    }
}
