pipeline{
    agent{
        node{
            label 'linux && go'
        }
    }
    stages {
        stage('build'){
            steps{
                sh 'go build -o main cmd/app/main.go'
            }
        }
        stage('test'){
            steps{
                echo "test ${env.JOB_NAME}"
            }
        }
        stage('deploy'){
            steps{
                echo "deploy ${env.JOB_NAME}"
            }
        }
    }
    post{
        success{
            slackSend(message: "${env.JOB_NAME} - ${env.BUILD_DISPLAY_NAME} Success after ${currentBuild.duration} ms (<${env.BUILD_URL}|Open>)")
        }
        failure{
            slackSend(message: "${env.JOB_NAME} - ${env.BUILD_DISPLAY_NAME} Failure after ${currentBuild.duration} ms (<${env.BUILD_URL}|Open>)")
        }
    }
}