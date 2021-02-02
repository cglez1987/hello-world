pipeline {
    agent none
    environment{
        TEMP = ''
    }
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
                    if ("${env.GIT_BRANCH}" == 'master')
                    {
                        echo "This is a master change"
                        TEMP = "carlos"
                        echo "TEMP value is: ${TEMP}"
                    }
                    else
                    {
                        echo "Nop........!!!!"
                        TEMP = "joseee"
                    }
                    sh 'ls -l | grep "${TEMP}"'
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
