pipeline {
  agent { docker { image 'maven:3.9-eclipse-temurin-17' } }
  options { skipDefaultCheckout(false) }
  stages {
    stage('Build & Test') {
      steps {
        sh 'mvn -B -e -DskipTests=false clean package'
      }
    }
  }
  post {
    always {
      junit '**/target/surefire-reports/*.xml'
      archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
    }
  }
}