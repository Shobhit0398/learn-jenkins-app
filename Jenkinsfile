pipeline {
    agent any
    environment {
        PATH = "${DOCKER_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                    ls -la
                    node --version
                    docker --version
                    docker pull node:18-alpine
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
        }
    }
}
