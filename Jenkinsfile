pipeline{
    agent{
        label 'agent0'
    }
    tools{
        maven 'mvn3.8.1'
    }
    environment{
        Image_tag="10"
    }
    stages{
        stage('maven version'){
            steps{
                sh "mvn -v"
            }
        }
    }
}
