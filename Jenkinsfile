pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        warnError(message: 'FUNTIONAL PROBLEMSI ERREUR ') {
          sh 'dotnet build eShopOnWeb.sln'
        }

      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('Funtional') {
          steps {
            sh 'dotnet test tests/FuntionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}