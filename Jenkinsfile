pipeline {
    agent any  // Usa cualquier agente disponible (el nodo donde Jenkins se está ejecutando)

    // Solo construir si estamos en la rama "feature"
    triggers {
        pollSCM('* * * * *')  // (opcional) revisa cada minuto si hay cambios en el repositorio
    }

    options {
        skipStagesAfterUnstable() // (opcional) para detener si algo falla
    }

    stages {
        stage('Checkout') {
            steps {
                // Clonar el código de la rama feature
                git branch: 'feature', url: 'https://turepositorio.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Construyendo el proyecto...'
                // Aquí podrías poner tu comando real de build, por ejemplo:
                // sh './build.sh' o 'mvn package' o 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando tests...'
                // Ejemplo: sh 'npm test' o 'pytest tests/'
            }
        }
    }

    post {
        success {
            echo 'El pipeline se ejecutó correctamente.'
        }
        failure {
            echo 'El pipeline falló.'
        }
    }
}
