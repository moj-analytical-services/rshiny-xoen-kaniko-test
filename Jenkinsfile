node {
    checkout scm

    env.REPO_NAME = sh(
        script: "echo $env.JOB_NAME | cut -f 2 -d /",
        returnStdout: true
    ).trim()

    stage('Configure Docker registry') {
        withCredentials([usernamePassword(credentialsId: 'aws-ecr',
                                          passwordVariable: 'AWS_SECRET_ACCESS_KEY',
                                          usernameVariable: 'AWS_ACCESS_KEY_ID')]) {

            // def REPO_NAME = repoName()

            // sh "echo $JOB_NAME | cut -f 2 -d /"

            sh "echo $REPO_NAME"

            // sh """
            // echo ${env.JOB_NAME}
            // echo ${env.JOB_BASE_NAME}
            // """

            // sh '''
            // aws configure set default.region eu-west-1
            // aws configure set aws_access_key_id $AWS_SECRET_ACCESS_KEY
            // aws configure set aws_secret_access_key $AWS_ACCESS_KEY_ID

            // if ! aws ecr describe-repositories --repository-names ${env.REPO_NAME} > /dev/null 2>&1; then
            //     aws ecr create-repository --repository-name ${env.REPO_NAME};
            // fi
            // '''
        }
    }
    stage('Build') {
        echo 'Building..'
    }
    stage('Deploy') {
        echo 'Deploying....'
    }
}

// def repoName(jobName) {
//     sh(
//         script: "echo $JOB_NAME | cut -f 2 -d /",
//         returnStdout: true
//     ).trim()
// }
