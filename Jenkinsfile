def setBuildStatus(String message, String state, String context, String sha) {  
    step([
        $class: "GitHubCommitStatusSetter",        
        contextSource: [$class: "ManuallyEnteredCommitContextSource", context: context],        
        statusResultSource: [$class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
} 
pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL} on ${env.BRANCH_NAME} and ${env.GIT_COMMIT}"
                echo 'Building..'
                setBuildStatus("In Progresss","SUCCESS","jenkins-pipeline-git",env.GIT_COMMIT )
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                 setGitHubPullRequestStatus context: 'jenkins-pipeline-git', message: 'Results', state: 'SUCCESS'
                setBuildStatus("In Progresss","SUCCESS","jenkins-pipeline-git",env.GIT_COMMIT )
                setBuildStatus("In Progresss","SUCCESS","asdfasdfasdf",env.GIT_COMMIT )
                setGitHubPullRequestStatus context: 'kkkkkk', message: 'Results', state: 'SUCCESS'
            }
            
        }
    }
}
