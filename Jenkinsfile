pipeline {
    agent { label 'test' }
    tools {
        maven 'maven 1.8'
        jdk 'jdk8'
    }
    stages {
        stage('Build JAR') {
            steps {
                  sh "mvn clean install"
            }
        }
        stage('Artifacts JAR') {
            steps {
                 archiveArtifacts artifacts: 'target/*.jar'
            }
        }
        stage('Build Image'){
            steps {
                sh "docker build -t hassaneid/java:${BUILD_NUMBER} ."
            }
                
        }
        //stage('Scan') {
          //  steps {
          //      sh "docker scan hassaneid/java:${BUILD_NUMBER} >> scanresult.txt | set +e"
        //
        //    }
        //}
       // stage('Publish') {
         //   steps {
           //    sh 'docker push hassaneid/java:${BUILD_NUMBER}'
           // }
       // }
       // stage('Deploy'){
         //   steps {
           //     sh """ ssh -i /home/ec2-user/eand.pem ec2-user@52.91.25.97 'sudo kubectl set image deployment java-deployment java=hassaneid/java:${BUILD_NUMBER}' """
           // } 
       // }

    }
}
