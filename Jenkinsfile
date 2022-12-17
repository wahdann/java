pipeline {
    agent any
    stages {
        stage('Build JAR') {
            steps {
                  sh "mvn clean install -DskipTests=true"
            }
        }
        stage('Artifacts JAR') {
            steps {
                 archiveArtifacts artifacts: 'target/*.jar'
            }
        }
        // stage('Test') {
        //     steps {
        //           sh "mvn test"
        //     }
        //     post { 
        //         always { 
        //             junit 'target/surefire-reports/*.xml'
        //             jacoco execPattern: 'target/jacoco.exec'
        //                 }
        //          }
        // }
        stage('Build Image'){
            steps {
                sh "docker build -t 192.168.205.141:5000/repository/app/java:${BUILD_NUMBER} ."
                sh "docker login -u admin -p 123 192.168.205.141:5000"
                sh "docker push 192.168.205.141:5000/repository/app/java:${BUILD_NUMBER}"
            }
        }
        // stage('Scan') {
        //    steps {
        //        sh "docker scan hassaneid/java:${BUILD_NUMBER} >> scanresult.txt | set +e"
        
        //    }
        // }
    //    stage('Deploy'){
    //        steps {
    //            sh """ ssh -i /home/ec2-user/eand.pem ec2-user@52.91.25.97 'sudo kubectl set image deployment java-deployment java=hassaneid/java:${BUILD_NUMBER}' """
    //        } 
    //    }
    }
}
