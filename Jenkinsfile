pipeline{
    agent{
        node{
            label 'linux && go'
        }
    }
    triggers{
        pollSCM("* * * * *")
    }
    options{
        buildDiscarder(logRotator(numToKeepStr: '3'))
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
            slackSend(color: "good", message: "${env.JOB_NAME} - ${env.BUILD_DISPLAY_NAME} Success after ${currentBuild.durationString.replace(' and counting', '')} (<${env.BUILD_URL}|Open>)")
        }
        failure{
            slackSend(color: "danger", message: "${env.JOB_NAME} - ${env.BUILD_DISPLAY_NAME} Failure after ${currentBuild.durationString.replace(' and counting', '')} (<${env.BUILD_URL}|Open>)")
        }
    }
}