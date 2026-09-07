pipeline {
    agent any

    stages {
        stage('Instalar Dependencias') {
            steps {
                echo 'Instalando dependencias do projeto...'
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Executando build do projeto...'
                bat 'npm run build'
            }
        }

        stage('Teste') {
            steps {
                echo 'Executando testes automatizados...'
                bat 'npm test'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executado com sucesso!'
        }

        failure {
            echo 'Pipeline falhou! Verifique os logs.'
        }
    }
}
