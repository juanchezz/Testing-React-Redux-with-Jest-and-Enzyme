pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Compilando el proyecto...'
            }
        }
        stage('Test') {
            steps {
                echo 'Ejecutando tests...'
            }
        }
    }

    // Opcional: solo ejecutar en la rama feature
    triggers {
        pollSCM('* * * * *')
    }

    options {
        skipDefaultCheckout true
    }

    environment {
    }

    post {
        always {
            echo 'Pipeline finalizado (éxito o fallo).'
        }
    }
}
