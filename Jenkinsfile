pipeline {
    agent {
        docker {
            image 'node:18'
        }
    }

    triggers {
        pollSCM('H/15 * * * *') // Revisión automática cada 15 minutos
    }

    environment {
        NODE_ENV = 'production'
        DEPLOY_DIR = '/var/www/miapp'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/juanchezz/Testing-React-Redux-with-Jest-and-Enzyme.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    mkdir -p $DEPLOY_DIR
                    rm -rf $DEPLOY_DIR/*
                    cp -r build/* $DEPLOY_DIR/
                '''
            }
        }
    }

    post {
        success {
            echo 'Despliegue exitoso'
        }
        failure {
            echo 'Algo falló en el pipeline'
        }
    }
}
