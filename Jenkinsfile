pipeline {
  agent any
  stages {
    stage('Print Message') {
      steps {
        echo 'This is a test'
      }
    }
    stage('Build') {
      steps {
        bat "\"${tool 'MSBuild'}\\msbuild.exe\" \"TestWebApplication\\TestWebApplication.sln\" /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
      }
    }
    stage('Archive') {
      steps {
        archiveArtifacts 'TestWebApplication\\TestWebApplication\\bin'
      }
    }
  }
}
