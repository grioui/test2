def project = "projet1"
def outputPath = "C:\\Users\\hgrioui\\source\\repos\\res\\p1"
def msbuild = tool name: 'MSBuild', type: 'hudson.plugins.msbuild.MsBuildInstallation'

pipeline {
    agent any
    parameters {
        booleanParam(name: 'deployToProd', defaultValue: false, description: 'Déployer en production ?')
        booleanParam(name: 'deployToRecette', defaultValue: false, description: 'Déployer en recette ?')
        string(name: 'buildNumber', defaultValue: '-1', description: 'Numéro de version à utiliser pour la version de production')
        string(name: 'DEPLOY_ENV', defaultValue: 'Release', description: 'environnement de déploiement')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build & SonarQube analysis') {
            steps {
                echo "Building ..."
                bat "${msbuild} ${project}.sln /p:OutputPath=${outputPath} /p:Platform=\"Any CPU\""
            }
        }
    }
}
