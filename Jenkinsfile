pipeline{
    agent {
        label 'java'
    }

    tools{
        jdk "java-8"
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