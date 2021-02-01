pipeline {
    agent none
    stages{
        stage("Validate terraform") {
            agent {
                docker { image 'hashicorp/terraform:latest'}
            }
            steps{
                echo "========Validating files========"
                sh 'cd /dev'
                sh 'terraform validate'
            }
        }
        stage("Test") { 
            steps{
                echo "====++ Testing with terratest ++++===="
            }
        }
    }
}
