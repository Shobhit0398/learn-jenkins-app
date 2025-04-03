pipeline {
    agent any
    environment {
        DOCKER_HOME = tool name: 'myDocker', type: 'DockerTool'
        PATH = "${DOCKER_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
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
        }
    }
}
