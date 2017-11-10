def setGithubStatus(String message, String state, String context, String sha) { 
    step([
        $class: "GitHubCommitStatusSetter",      
        reposSource: [$class: "ManuallyEnteredRepositorySource", url: ""],
        contextSource: [$class: "ManuallyEnteredCommitContextSource", context: context],  
        commitShaSource: [$class: "ManuallyEnteredShaSource", sha: sha ],
        statusResultSource: [$class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
} 

node{
  
        stage('Build') {
                checkout scm
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL} on ${env.BRANCH_NAME} and ${env.GIT_COMMIT}"
                sh 'git rev-parse HEAD > commit'
                def commit = readFile('commit').trim()
                def GIT_COMMIT_HASH = sh (script: "git log -n 1 --pretty=format:'%H'", returnStdout: true)
                echo "Building.. ${commit} .. ${GIT_COMMIT_HASH}"
                setGithubStatus("In Progresss","SUCCESS","jenkins-pipeline-git", "${commit}")
            
        }
        stage('Test') {
                 echo 'Testing..'            
        }
        stage('Deploy') {
             def GIT_COMMIT_HASH = sh (script: "git log -n 1 --pretty=format:'%H'", returnStdout: true)
             echo 'Deploying.... ${GIT_COMMIT_HASH}'
                // setGitHubPullRequestStatus context: 'jenkins-pipeline-git', message: 'Results', state: 'SUCCESS'
             step([
        $class: "GitHubCommitStatusSetter",      
        reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/hassan-jamous/test/"],
        contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "hi"],  
        commitShaSource: [$class: "ManuallyEnteredShaSource", sha: "${GIT_COMMIT_HASH}" ],
        statusResultSource: [$class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: "asdfasdf", state: "SUCCESS"]] ]
    ]);

                setGithubStatus("In Progresss","SUCCESS","jenkins-pipeline-git",  "${GIT_COMMIT_HASH}")
                setGithubStatus("In Progresss","SUCCESS","asdfasdfasdf", "${GIT_COMMIT_HASH}")
               // setGitHubPullRequestStatus context: 'kkkkkk', message: 'Results', state: 'SUCCESS'
        }
}
   

