pipeline{
  agent any
  tools {
    maven 'maven3'
  }
  stages {
    stage('Build') {
      steps{
          bat'mvn -B -DskipTests clean package'
      }
    }
    stage('Test'){
      steps {
          bat 'mvn test'
      }
      post {
        always {
          junit skipPublishingChecks: true, testResults: 'target/surefire-reports/*.xml'
        }
      }
    }
    stage('Deliver') {
      steps {
          bat 'echo "Delivering project..."'
      }
    }
  }
}
