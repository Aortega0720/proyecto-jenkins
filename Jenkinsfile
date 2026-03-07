pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Clonando el repositorio desde GitHub...'
                git url: 'https://github.com/Aortega0720/proyecto-jenkins.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Construyendo la aplicación...'
                sh 'echo "Build completado"'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
                sh 'echo "Tests ejecutados correctamente"'
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
            echo 'Pipeline ejecutado exitosamente'
        }
        failure {
            echo 'El pipeline falló'
        }
    }

}