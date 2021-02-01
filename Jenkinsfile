pipeline {
    agent none
    stages{
        stage("Validate terraform") {
            agent {
                docker { image 'hashicorp/terraform:light'}
            }
            steps{
                echo "========Validating files========"
                sh 'cd /dev'
                sh 'validate'
            }
        }
        stage("Test") { 
            steps{
                echo "====++ Testing with terratest ++++===="
            }
        }
    }
}
