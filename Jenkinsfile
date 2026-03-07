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
            agent {
                docker {
                    image 'python:3.10'
                }
            }
            steps {
                echo 'Instalando dependencias...'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'python:3.10'
                }
            }
            steps {
                echo 'Ejecutando pruebas...'
                sh 'pytest'
            }
        }

        stage('Deploy Simulation') {
            steps {
                echo 'Simulando despliegue...'
                sh 'echo "Aplicación desplegada correctamente (simulación)"'
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado exitosamente'
        }
        failure {
            echo 'Error en el pipeline'
        }
    }
}