pipeline {

    agent any

    environment {
        REPO = 'https://github.com/Aortega0720/proyecto-jenkins.git'
        BRANCH = 'main'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Clonando el repositorio...'
                git url: "${REPO}", branch: "${BRANCH}"
            }
        }

        stage('Build') {
            steps {
                echo 'Instalando dependencias...'
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
                sh '''
                    . venv/bin/activate
                    pytest
                '''
            }
        }

        stage('Deploy Simulation') {
            steps {
                echo 'Simulando despliegue...'
                sh '''
                    echo "Aplicación desplegada en entorno simulado"
                '''
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