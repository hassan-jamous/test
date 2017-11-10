
def setGithubStatus(String message, String state, String context) { 
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
                setGithubStatus("In Progresss","SUCCESS","jenkins-pipeline-git")
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            if (true) {
            setGitHubPullRequestStatus context: 'jenkins-pipeline-git', message: 'Results', state: 'SUCCESS'
            }
            steps {
                echo 'Deploying....'
                
                setGithubStatus("In Progresss","SUCCESS","jenkins-pipeline-git")
                setGithubStatus("In Progresss","SUCCESS","asdfasdfasdf")
                setGitHubPullRequestStatus context: 'kkkkkk', message: 'Results', state: 'SUCCESS'
            }
            
        }
    }
}
