pipeline {
  agent any
  stages {
    stage('compile') {
      steps {
        sh 'gradlew clean compileJava test'
      }
    }

    stage('echo') {
      steps {
        echo 'Hola'
      }
    }

  }
}