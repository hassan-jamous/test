
def setBuildStatus(String message, String state, String context, String sha) {  
    step([
        $class: "GitHubCommitStatusSetter",
        reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/hassan-jamous/test"],
        contextSource: [$class: "ManuallyEnteredCommitContextSource", context: context],
        errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
        commitShaSource: [$class: "ManuallyEnteredShaSource", sha: sha ],
        statusBackrefSource: [$class: "ManuallyEnteredBackrefSource", backref: "${BUILD_URL}flowGraphTable/"],
        statusResultSource: [$class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
} 
node {

    stages {
        stage('Build') {
            
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL} on ${env.BRANCH_NAME} and ${env.GIT_COMMIT}"
                echo 'Building..'
                setBuildStatus("In Progress Build","PENDING","jenkins-pipeline",env.GIT_COMMIT )
                for (i = 0; i <500; i++) {
                    echo 'Results Hello World'
                }
            
        }
        stage('Test') {
            
                echo 'Testing..'
                setBuildStatus("In Progress Test","PENDING","jenkins-pipeline",env.GIT_COMMIT )
                for (i = 0; i <500; i++) {
                    echo 'Results Hello World'
                } 
                setBuildStatus("In Progress Test","PENDING","jenkins-pipeline",env.GIT_COMMIT )           
           
        }
        stage('Deploy') {
            
            setBuildStatus("In Progress Deploy","PENDING","jenkins-pipeline",env.GIT_COMMIT )
            for (i = 0; i <500; i++) {
                    echo 'Results Hello World'
                } 
            setBuildStatus("Doneeeee","SUCCESS","jenkins-pipeline",env.GIT_COMMIT )    
           
                echo 'Deploying....'
            
            
        }
    }
}
