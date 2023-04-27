pipeline {
  agent any
  stages {
    stage('Compilation') {
      steps {
        sh 'chmod +x gradlew'
        sh './gradlew clean build'
      }
    }
    stage('Run Spotless') {
      steps {
          script {
              // Run Spotless
              sh './gradlew spotlessApply'
          }
      }
    }
  }
  post {
    always {
      archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
    }
  }
}