pipeline {
    agent any
    
    triggers {
        pollSCM('H/2 * * * *') 
        // Jenkins revisa cada 2 minutos si hay cambios en el repo
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Haciendo checkout del repo...'
                git branch: 'main', url: 'https://github.com/franpar410/hades-master.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Este es un build de prueba'
                sh 'echo "Hola desde Jenkins!"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy ficticio...'
            }
        }
    }
}