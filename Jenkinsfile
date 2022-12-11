pipeline{
    agent{
        node{
            label 'linux && go'
        }
    }
    stages {
        stage('build'){
            steps{
                sh 'go build -o /cmd/app/main.go'
            }
        }
        stage('test'){
            steps{
                echo "test ${env.BRANCH_NAME}"
            }
        }
        stage('deploy'){
            steps{
                echo "deploy ${env.BRANCH_NAME}"
            }
        }
    }
    post{
        success{
            slackSend "${env.JOB_NAME} - ${env.BUILD_DISPLAY_NAME} Success after ${currentBuild.duration} ms (<${env.BUILD_URL}|Open>)"
        }
    }
}