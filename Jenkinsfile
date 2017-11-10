def setGithubStatus(String message, String state, String context, String sha) { 
    step([
        $class: "GitHubCommitStatusSetter",        
        contextSource: [$class: "ManuallyEnteredCommitContextSource", context: context],  
        commitShaSource: [$class: "ManuallyEnteredShaSource", sha: sha ],
        statusResultSource: [$class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
} 
pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL} on ${env.BRANCH_NAME} and ${env.GIT_COMMIT}"
                GIT_COMMIT_HASH = sh (script: "git log -n 1 --pretty=format:'%H'", returnStdout: true)
                echo 'Building.. ${GIT_COMMIT_HASH}'
                setGithubStatus("In Progresss","SUCCESS","jenkins-pipeline-git", "${env.GIT_COMMIT}")
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
                setGithubStatus("In Progresss","SUCCESS","jenkins-pipeline-git",  "${env.GIT_COMMIT}")
                setGithubStatus("In Progresss","SUCCESS","asdfasdfasdf", "${env.GIT_COMMIT}")
                setGitHubPullRequestStatus context: 'kkkkkk', message: 'Results', state: 'SUCCESS'
            }
            
        }
    }
}
