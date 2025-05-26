pipeline{
    agent {
        label 'agent-0'
    }

    tools{
        jdk "java-8"
    }

    parameters {
        string defaultValue: '${BUILD_NUMBER}', description: 'Enter the version of the docker image', name: 'VERSION'
        choice choices: ['true', 'false'], description: 'Skip test', name: 'TEST'
    }

    stages{
        stage("Build java app"){
            steps{
                sh "mvn clean package install -Dmaven.test.skip=${TEST}"
            }
        }
        stage("build java app image"){
            steps{
                sh "docker build -t java:v${VERSION} ."
            }
        }
    }
    
}