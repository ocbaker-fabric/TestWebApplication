pipeline {
  agent any
  stages {
    stage('Print Message') {
      parallel {
        stage('Print Message') {
          steps {
            echo 'This is a test'
          }
        }
        stage('List Files') {
          steps {
            bat 'dir'
          }
        }
      }
    }
    stage('Build') {
      steps {
        bat 'nuget restore TestWebApplication.sln'
        bat "\"${tool 'MSBuild'}\\msbuild.exe\" \"TestWebApplication.sln\" /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
      }
    }
    stage('Archive') {
      steps {
        archiveArtifacts 'TestWebApplication\\TestWebApplication\\bin'
      }
    }
  }
}
