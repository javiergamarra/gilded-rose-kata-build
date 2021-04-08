pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
               git branch: 'dev', url: 'https://github.com/nhpatt/gilded-rose-kata-build.git'
            }
        }
        stage('Compile') {
            steps {
               sh './gradlew clean compileJava'
            }
        }
        stage('test') {
            parallel {
                stage('test unitarios') {
                    steps {
                         sh './gradlew test'
                    }
                }
                stage('tests integracion') {
                    steps {
                        sleep 1
                    }
                }
                stage('check') {
                    steps {
                        sleep 1
                    }
                }
                stage('check1') {
                    steps {
                        sleep 1
                    }
                }
            }
        }
        stage('Desplegar') {
            options {
                timeout(time: 10, unit: 'SECONDS')
            }
            input {
                message '¿Despliegue a preproduccion?'
                ok 'SI'
                parameters {
                    booleanParam(defaultValue: false, description: 'Borrar base de datos', name: 'BD')
                }
            }
            steps {
                echo "Borrando: ${BD}"   
            }
        }
    }
    post {
      always {
       junit 'build/**/*.xml'
      }
    }
}

