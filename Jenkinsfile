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
                script{
                    echo "preparing environment"
                    if (System.getenv("GIT_BRANCH") == 'master')
                        echo "This is a master change"
                    else
                        echo "Nop........!!!!"
                    sh 'aws --version'
                }
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
                echo "========Initializing terraform modules========"
                sh 'cd network'
                sh 'terraform init'
            }
        }
        stage("Validation") { 
            when {branch 'master'}
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
