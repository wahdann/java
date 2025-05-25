pipeline{
    agent {
        label 'java'
    }

    stages{
        stage("Build java app"){
            steps{
                tool name: 'java-8', type: 'jdk'
                sh 'mvn clean package install'
            }
        }
        stage("Test java app"){
            steps{
                tool name: 'java-8', type: 'jdk'
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