pipeline {
  agent any
  tools {
      jdk 'jdk17'
  }
  stages {
   stage('JAVA') {
      steps {
        sh 'java -version'
      }
    }
    stage('Compilation') {
      steps {
        sh 'chmod +x gradlew'
        sh './gradlew clean build'
      }
    }
  }
  post {
    always {
      archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
    }
  }
}