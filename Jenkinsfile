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
                echo 'Ejecutando pruebas con pytest...'
                sh '''
                . venv/bin/activate
                pytest tests/
                '''
            }
        }

        stage('Deploy Simulation') {
            steps {
                echo 'Simulando despliegue de la aplicación...'
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