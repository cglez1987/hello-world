pipeline {
    agent none
    stages{
        stage("Validate terraform") {
            agent {
                docker {
                   image 'maven:3-alpine'
                   args  "--entrypoint=''"
                }
            }
            steps{
                echo "========Validating files========"
                sh 'validate'
            }
        }
    }
}
