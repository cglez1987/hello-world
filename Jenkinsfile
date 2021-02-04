pipeline {
    agent any
    environment{
        TEMP = 'network'
    }
    stages{
        stage("test"){
            steps{
                dir("${TEMP}"){
                    sh 'ls -l'
                }
                echo "Testing tagging strategy"
                sh 'ls -l'
            }
        }
        stage("Planification") { 
            when {branch 'master'}
            steps{
                echo "====++ Enter to planification stage ++++===="
                sh "git tag -a v1.1 -m ${BUILD_TAG}"
				sh "git push --tags origin"
            }
        }
	}
}
