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

            steps {
                sh '''
                    docker images
                '''
            }
        }
    }
}
