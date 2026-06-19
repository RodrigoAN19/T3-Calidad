pipeline {
    agent any
    stages {
        stage('Clonar') {
            steps { checkout scm }
        }
        stage('Restaurar') {
            steps { bat 'dotnet restore MiSolucion.sln' }
        }
        stage('Compilar') {
            steps { bat 'dotnet build MiSolucion.sln --configuration Release' }
        }
        stage('Pruebas') {
            steps { bat 'dotnet test MiSolucion.sln --no-build' }
        }
        stage('Publicar') {
            steps { bat 'dotnet publish MiAppWeb.csproj --configuration Release --output ./publish' }
        }
    }
    post {
        success { echo 'Pipeline OK' }
        failure { echo 'Pipeline FALLO' }
    }
}