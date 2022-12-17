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
                sh "docker push 192.168.205.141:5000/repository/app/java:${BUILD_NUMBER}"
            }
        }
        // stage('Scan') {
        //    steps {
        //        sh "docker scan hassaneid/java:${BUILD_NUMBER} >> scanresult.txt | set +e"
        
        //    }
        // }
        // stage('Deploy'){
        //     steps {
        //         sh """ ssh -i /home/ec2-user/eand.pem ec2-user@52.91.25.97 'sudo kubectl set image deployment java-deployment java=hassaneid/java:${BUILD_NUMBER}' """
        //     } 
        // }
        stage('Update GIT'){ 
            steps{
                script {

                    sh """
                    if [ -d enviroment-repo-argocd ]; then
                    git clone \
                    --depth 1 \
                    --filter=blob:none \
                    --no-checkout \
                    https://github.com/Hassan-Eid-Hassan/enviroment-repo-argocd.git \
                    ;
                    cd enviroment-repo-argocd
                    git checkout main -- java
                    else; 
                    cd enviroment-repo-argocd
                    git checkout main -- java
                    fi;
                    cat ./java/deployment.yaml
                    sed -i 's|REPLACE|${BUILD_NUMBER}|g' ./java/deployment.yaml
                    cat ./java/deployment.yaml
                    git add .
                    git commit -m 'Done by Jenkins Job changemanifest by user : ${env.BUILD_USER}'
                    git push https://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@github.com/Hassan-Eid-Hassan/enviroment-repo-argocd.git HEAD:main
                    """
                }
            }
        }
    }
}
