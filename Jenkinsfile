pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Clonando repositorio...'
                deleteDir()
                git url: 'https://github.com/Aortega0720/proyecto-jenkins.git', branch: 'main'
                sh 'ls -la'
            }
        }

        stage('Build') {
            steps {
                echo 'Instalando dependencias...'
                sh '''
                docker run --rm \
                -v $(pwd):/app \
                -w /app \
                python:3.10 \
                bash -c "ls -la && pip install -r requirements.txt"
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
                bash -c "pytest tests/"
                '''
            }
        }

        stage('Deploy Simulation') {
            steps {
                echo 'Simulando deploy...'
                sh 'echo "Aplicación iniciada (simulación)"'
            }
        }

    }

    post {
        success {
            echo 'Pipeline ejecutado exitosamente'
        }
        failure {
            echo 'El pipeline falló. Revisar errores en consola.'
        }
    }
}