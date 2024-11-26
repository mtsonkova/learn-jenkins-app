pipeline {
    agent any

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
                    npm --version
                    npm ci
                    npm run build
                    ls -la
               '''
            }
        }

        stage('test') {
            steps {
                sh'''
                    echo "Test stage"
                    test "build/index.js"
                    npm run test
                '''
            }
        }
    }
}