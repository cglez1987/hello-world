pipeline {
    agent none
    stages{
        stage("Validate terraform") {
            agent {
                docker { image 'hashicorp/terraform:light'}
            }
            steps{
                echo "========Validating files========"
                sh 'validate'
            }
        }
    }
}
