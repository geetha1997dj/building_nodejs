prodUtiServer = "3.82.202.30"

pipeline {
    agent any

    stages {
        stage('git'){
            steps {
               git branch: 'main', url: 'https://github.com/vphanideep/building_nodejs.git'
            }
        }
        stage('Hello') {
            steps {
                sshagent(['awsserver']) {
                    echo "Hello world"
                    sh 'mkdir demo2'
                    sh(returnStatus: true , script: "scp -r ${env.WORKSPACE}/build.sh awsserver@${prodUtiServer}:/home/ec2-user")
                }
            }
        }
    }
}