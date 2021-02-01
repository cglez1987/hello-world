pipeline {
    agent {
        docker {
            image 'hashicorp/terraform:light'
            args  "--entrypoint=''"
        }
    }
    stages{
        stage("Initialization") {
            steps{
                echo "========Initializing terraform modules========"
                sh 'cd network'
                sh 'terraform init'
            }
        }
        stage("Validation") { 
            steps{
                echo "====++ Validate terraform files ++++===="
                sh 'terraform validate'
            }
        }
        stage("Planification") { 
            when {branch 'master'}
            steps{
                echo "====++ Enter to planification stage ++++===="
                sh 'terraform plan'
            }
        }
    }
}
