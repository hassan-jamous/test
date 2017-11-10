def setGithubStatus(String message, String state, String context, String sha) { 
    step([
        $class: "GitHubCommitStatusSetter",        
        contextSource: [$class: "ManuallyEnteredCommitContextSource", context: context],  
        commitShaSource: [$class: "ManuallyEnteredShaSource", sha: sha ],
        statusResultSource: [$class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
} 

node{
  
        stage('Build') {
            
           
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL} on ${env.BRANCH_NAME} and ${env.GIT_COMMIT}"
                sh 'git rev-parse HEAD > commit'
                def commit = readFile('commit').trim()
                echo "Building.. ${commit}"
                setGithubStatus("In Progresss","SUCCESS","jenkins-pipeline-git", "${env.GIT_COMMIT}")
            
        }
        stage('Test') {
            
                
                echo 'Testing..'
            
        }
        stage('Deploy') {
           
                echo 'Deploying....'
                 setGitHubPullRequestStatus context: 'jenkins-pipeline-git', message: 'Results', state: 'SUCCESS'
                setGithubStatus("In Progresss","SUCCESS","jenkins-pipeline-git",  "${env.GIT_COMMIT}")
                setGithubStatus("In Progresss","SUCCESS","asdfasdfasdf", "${env.GIT_COMMIT}")
                setGitHubPullRequestStatus context: 'kkkkkk', message: 'Results', state: 'SUCCESS'
            
            
        }
}
   

