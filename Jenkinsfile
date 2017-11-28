#!groovy
def setGithubStatus(String message, String state, String context, String sha) { 
    step([
        $class: "GitHubCommitStatusSetter",      
        reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/hassan-jamous/test"],
        contextSource: [$class: "ManuallyEnteredCommitContextSource", context: context],  
        commitShaSource: [$class: "ManuallyEnteredShaSource", sha: sha ],
        statusResultSource: [$class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
} 

def getCukeEnvironment(String fullEnvironmentName) {
    def envNameStartIndex = fullEnvironmentName.indexOf("-mlc") + 4;
    def envNameEndIndex = fullEnvironmentName.indexOf("-", envNameStartIndex)
    def environmentName = fullEnvironmentName.substring(envNameStartIndex, envNameEndIndex);
    return "e2e.cuke.environments." + environmentName + ".js"
}

def getCukeTags(String branchName) {
    def jsonTagFile = 
    def  = new groovy.json.JsonSlurperClassic().parseText(readFile('tags.json'));
    String tags = parssedTagsFile[branchName];   
    if (!tags) {
        tags = parssedTagsFile["default]
    }
    return tags;   
}

node{
  
        stage('Build') {
            checkout scm
               def cuke = getCukeEnvironment("ewcs-syd-f1-mlcnp5-15");
                echo "${cuke}"
            
            def cukeTags = getCukeTags("hassan-jamous-patch-13");
                echo "${cukeTags}"
            
            
        }
        stage('Test') {
                 echo 'Testing..'            
        }
        stage('Deploy') {
            
        }
}
   

