pipeline{
    agent{
        label 'agent0'
    }
    tools{
        maven 'mvn3.9.0'
    }
    environment{
        Image_tag="10"
    }
    stages{
        stage('Clean'){
            steps{
                sh "mvn clean"
            }
        }
        stage('Build JAR') {
            steps {
                  sh "mvn install"
            }
        }
        // stage('Artifacts JAR') {
        //     steps {
        //          archiveArtifacts artifacts: 'target/*.jar'
        //     }
        // }
    }
}
