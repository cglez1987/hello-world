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
        stage("Release"){
            environment { 
				GIT_AUTH = credentials('GitHub-UserPass') 
			}
            steps{
                echo "====++++Creating release with tag++++===="
                script{
                    tagVersion = input(id: 'tagVersion', message: 'Enter the tag version: ', parameters: [string(defaultValue: '', description: '', name: 'Tag Version')])
                }
				sh "git config --local credential.helper '!f() { echo username=\\$GIT_AUTH_USR; echo password=\\$GIT_AUTH_PSW; }; f'"
                sh  "git fetch --tags"
				sh  "git tag -a ${tagVersion} -m ${BUILD_TAG}"
				sh	"git push --tags origin"
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
