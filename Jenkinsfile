pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Clonando el repositorio...'
                git url: 'https://github.com/Aortega0720/proyecto-jenkins.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Instalando dependencias con Docker Python...'
                sh '''
                    docker run --rm \
                    -v $(pwd):/app \
                    -w /app \
                    python:3.10 \
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
                sh '''
                    docker run --rm \
                    -v $(pwd):/app \
                    -w /app \
                    python:3.10 \
                    pytest
                '''
            }
        }

        stage('Deploy Simulation') {
            steps {
                echo 'Simulando despliegue...'
                sh 'echo "Aplicación desplegada (simulación)"'
            }
        }

    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente'
        }
        failure {
            echo 'Error en el pipeline'
        }
    }

}