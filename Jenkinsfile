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
			environment { 
				GIT_AUTH = credentials('GitHub') 
			}
            steps{
				sh('''
					git config --local credential.helper "!f() { echo username=\\$GIT_AUTH_USR; echo password=\\$GIT_AUTH_PSW; }; f"
				    git tag -a v1.8 -m ${BUILD_TAG}
					git push --tags origin
				''')
            }
        }
	}
	post{
        always{
            echo 'Cleaning the workspace'
            cleanWs()
        }
    }
}
