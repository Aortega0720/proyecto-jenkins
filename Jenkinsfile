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
                echo 'Instalando dependencias en contenedor Python...'
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
                echo 'Ejecutando pruebas con pytest...'
                sh '''
                docker run --rm \
                -v $(pwd):/app \
                -w /app \
                python:3.10 \
                pytest tests/
                '''
            }
        }

        stage('Deploy Simulation') {
            steps {
                echo 'Simulando despliegue...'
                sh 'echo "Deploy simulado correctamente"'
            }
        }

    }

    post {
        success {
            echo 'Pipeline ejecutado exitosamente'
        }
        failure {
            echo 'El pipeline falló'
        }
    }
}