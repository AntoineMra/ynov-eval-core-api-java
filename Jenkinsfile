pipeline {
  agent any
  stages {
    // stage('Install Spotless plugin') {
    //   steps {
    //       script {
    //           // Install the Spotless plugin
    //           def plugin = Jenkins.instance.pluginManager.plugins.find { it.shortName == 'spotless' }
    //           if (!plugin) {
    //               Jenkins.instance.updateCenter.installPlugin('spotless')
    //               Jenkins.instance.restart()
    //           }
    //       }
    //   }
    // }
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