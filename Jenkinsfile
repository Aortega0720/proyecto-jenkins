pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                deleteDir()
                git url: 'https://github.com/Aortega0720/proyecto-jenkins.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Instalando dependencias...'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
                sh 'pytest tests/'
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