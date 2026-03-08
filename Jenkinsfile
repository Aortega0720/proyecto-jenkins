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

        stage('Build Image') {
            steps {
                echo 'Construyendo imagen Docker...'
                sh 'docker build -t fastapi-jenkins .'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
                sh 'docker run --rm fastapi-jenkins pytest tests/'
            }
        }

        stage('Deploy Simulation') {
            steps {
                echo 'Simulando despliegue...'
                sh 'docker run -d -p 8000:8000 fastapi-jenkins'
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