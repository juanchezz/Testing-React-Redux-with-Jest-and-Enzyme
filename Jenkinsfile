pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
        DEPLOY_DIR = '/var/www/miapp'  // Cambia esta ruta según dónde quieras desplegar
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/juanchezz/Testing-React-Redux-with-Jest-and-Enzyme.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Instalando dependencias...'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Construyendo la app...'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando tests...'
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando app en el contenedor...'
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
            echo 'CI/CD ejecutado correctamente ✅'
        }
        failure {
            echo 'Algo ha fallado en el pipeline ❌'
        }
    }
}
