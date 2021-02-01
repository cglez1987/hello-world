pipeline {
    agent none
    stages{
        stage("Prepare environment"){
            steps{
                echo "preparing environment"
            }
        }
        stage("Validate terraform") {
            agent {
                docker {
                   image 'hashicorp/terraform:light'
                   args  "--entrypoint=''"
                }
            }
            steps{
                echo "========Validating files========"
                sh 'cd network'
                sh 'terraform init'
                sh 'terraform validate'
            }
        }
    }
}
