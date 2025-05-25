pipeline{
    agent {
        label 'java'
    }

    tools{
        jdk "java-8"
    }

    environment {
        JAVA_HOME = "/home/jenkins/tools/hudson.model.JDK/java-8/openlogic-openjdk-8u442-b06-linux-x64"
    }

    stages{
        stage("Build java app"){
            steps{
                sh 'mvn clean package install'
            }
        }
        stage("Test java app"){
            steps{
                sh 'mvn test'
            }
        }
        stage("build java app image"){
            steps{
                sh 'docker build -t java:v1 .'
            }
        }
    }
    
}