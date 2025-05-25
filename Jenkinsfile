pipeline{
    agent {
        label 'java'
    }

    stages{
        stage("Build java app"){
            steps{
                sh 'echo "start building java app"'
            }
        }
        stage("Test java app"){
            steps{
                sh 'echo "Test java app"'
            }
        }
        stage("build java app image"){
            steps{
                sh 'echo "build java app image"'
            }
        }
    }
    
}