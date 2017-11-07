
def setBuildStatus(String message, String state, String context, String sha) {  
    step([
        $class: "GitHubCommitStatusSetter",
        reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/hassan-jamous/test"],
        contextSource: [$class: "ManuallyEnteredCommitContextSource", context: context],
        errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
        commitShaSource: [$class: "ManuallyEnteredShaSource", sha: env.GIT_COMMIT ],
        statusBackrefSource: [$class: "ManuallyEnteredBackrefSource", backref: "${BUILD_URL}flowGraphTable/"],
        statusResultSource: [$class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
}

node { 
   
   stage('Preparation') { 
       echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL} on ${env.BRANCH_NAME} and ${env.GIT_COMMIT}"
       /*step([$class: 'GitHubCommitStatusSetter', contextSource: [$class: 'ManuallyEnteredCommitContextSource',
                          context: 'jenkins-pipeline'],
           statusResultSource: [$class: 'ConditionalStatusResultSource',
                                results: [[$class: 'AnyBuildResult',
                                           message: 'test message',
                                          state: 'PENDING']]]])*/
                                          
        setBuildStatus("In Progress","PENDING","jenkins-pipeline",env.GIT_COMMIT )
                                          
                                          
     echo 'Preparation Hello World'
     
   }
   stage('Build') {
      echo 'Build Hello World'
      setGitHubPullRequestStatus context: 'jenkins-pipeline', message: 'Build', state: 'PENDING'
   }
   stage('Results') {
       /*for (i = 0; i <2000; i++) {
           echo 'Results Hello World'
        }*/
       setGitHubPullRequestStatus context: 'jenkins-pipeline', message: 'Results', state: 'SUCCESS'
   }
}
