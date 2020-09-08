def project = "${env.WORKSPACE}\\gitTest_master\\projet1\\projet1.csproj"
def outputPath = "C:\\Users\\hgrioui\\source\\repos\\res\\p1"

pipeline {
    agent any
    parameters {
        booleanParam(name: 'deployToProd', defaultValue: false, description: 'Déployer en production ?')
        booleanParam(name: 'deployToRecette', defaultValue: false, description: 'Déployer en recette ?')
        string(name: 'buildNumber', defaultValue: '-1', description: 'Numéro de version à utiliser pour la version de production')
        string(name: 'DEPLOY_ENV', defaultValue: 'Release', description: 'environnement de déploiement')
    }
     environment {
        MSBUILD = "C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Community\\MSBuild\\Current\\Bin\\MSBuild.exe"
        CONFIG = 'Release'
        PLATFORM = 'x64'
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
                bat "\"${MSBUILD}\"  ${project} /p:OutputPath=${outputPath} /p:Configuration=${env.CONFIG};Platform=\"Any CPU\""
            }
        }
    }
}
