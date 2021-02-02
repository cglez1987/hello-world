pipeline {
    agent any
    environment{
        TEMP = ''
    }
    stages{
        stage("test"){
            steps{
                dir("network"){
                    sh 'ls -l'
                }
                echo "Estoy afuera"
                sh 'ls -l'
            }
        }
    }
    /*
    stages{
        stage("Prepare environment"){
            steps{
                sh 'cd network'
                sh 'ls -l'
            }
        }
        stage("Get AWS parameters"){
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
                    sh "ls \$(ls -l | grep ${TEMP})"
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
                sh 'ls -l'
                sh 'terraform init'
                sh 'terraform plan'
            }
        }
        stage("Planification") { 
            when {branch 'master'}
            steps{
                echo "====++ Enter to planification stage ++++===="
                sh 'ls -l'
            }
        }
    }*/
}
