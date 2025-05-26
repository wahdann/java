pipeline{
    agent {
        label 'agent-0'
    }

    tools{
        jdk "java-8"
    }

    environment{
        DOCKER_USER = credentials('dockerhub-user')
        DOCKER_PASS = credentials('dockerhub-password')
    }

    parameters {
        string defaultValue: '${BUILD_NUMBER}', description: 'Enter the version of the docker image', name: 'VERSION'
        choice choices: ['true', 'false'], description: 'Skip test', name: 'TEST'
    }

    stages{
        parallel{
            stage("Build java app"){
                steps{
                    // parallel(
                    //     createFile: {
                    //         sh "touch ABCD"
                    //     },
                    //     buildJar:{
                            sh "mvn clean package install -Dmaven.test.skip=${TEST}"
                    //     }
                    // )
                }
            }
            stage("build java app image"){
                steps{
                    sh "docker login -u ${DOCKER_USER} -p ${DOCKER_PASS} "
                    sh "docker build -t java:v${VERSION} ."
                }
            }
        }
    }

    post{
        always{
            sh "echo 'Clean the Workspace'"
            cleanWs()
        }
        failure {
            sh "echo 'failed'"
        }
    }
}