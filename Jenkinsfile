pipeline {
    agent {
        docker { image 'hashicorp/terraform:latest'}
    }
    stages{
        stage("Validate terraform") {
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
