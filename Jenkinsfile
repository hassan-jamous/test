
def setGithubStatus(String message, String state, String context) { 
    step([
        $class: "GitHubCommitStatusSetter",        
        contextSource: [$class: "ManuallyEnteredCommitContextSource", context: context],        
        statusResultSource: [$class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
} 


        stage('Build') {
            node {
           
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL} on ${env.BRANCH_NAME} and ${env.GIT_COMMIT}"
                echo 'Building..'
            }
               // setGithubStatus("In Progresss","SUCCESS","jenkins-pipeline-git")
            
        }
        stage('Test') {
            node {
            
                echo 'Testing..'
            }
            
        }
        stage('Deploy') {  
            node {
                echo 'Deploying....'
                setGitHubPullRequestStatus context: 'jenkins-pipeline-git', message: 'Results', state: 'SUCCESS'
               // setGithubStatus("In Progresss","SUCCESS","jenkins-pipeline-git")
               // setGithubStatus("In Progresss","SUCCESS","asdfasdfasdf")
                setGitHubPullRequestStatus context: 'kkkkkk', message: 'Results', state: 'SUCCESS'
            }
            
            
        }

 

