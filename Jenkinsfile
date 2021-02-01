pipeline {
    agent none
    stages{
        stage("Prepare environment"){
            agent {
                docker {
                   image 'amazon/aws-cli'
                   args  "--entrypoint=''"
                }
            }
            steps{
                echo "preparing environment"
                sh 'aws --version'
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
