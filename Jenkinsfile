pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Compiling the project...'
        sh 'mvn compile'
      }
    }

    stage('Test') {
      steps {
        echo 'Running unit tests...'
        sh 'mvn clean test'
      }
    }

    stage('Package') {
      steps {
        echo 'Packaging the application...'
        sh 'mvn package -DskipTests'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.9.15'
  }
  post {
    success {
      echo 'Pipeline completed successfully!'
    }

    failure {
      echo 'Pipeline failed. Please check the logs.'
    }

  }
}