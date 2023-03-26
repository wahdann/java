pipeline{
    agent{
        label 'agent0'
    }
    tools{
        maven 'mvn3.9.0'
    }
    environment{
        SKIP_TEST='-DskipTests=true'
    }
    stages{
        stage('Clean'){
            steps{
                sh "mvn clean"
            }
        }
        stage('Build JAR') {
            steps {
                  sh "mvn install ${SKIP_TEST}"
            }
        }
        stage('Artifacts JAR') {
            steps {
                 archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }
}
