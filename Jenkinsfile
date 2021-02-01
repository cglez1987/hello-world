pipeline {
    agent none
    stages{
        stage("Validate terraform") {
            agent {
                docker {
                   image 'hashicorp/terraform:light'
                   args  "--entrypoint=''"
                }
            }
            steps{
                echo "========Validating files========"
                sh 'terraform validate'
            }
        }
    }
}
