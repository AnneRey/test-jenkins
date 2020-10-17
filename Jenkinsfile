node {
  
  stage ('Checkout'){
    checkout scm
  }

  stage ('Run when non PR') {
    if (!env.CHANGE_ID) {
      echo "Not a PR"
    }
  }
  
  stage ('Run when a PR triggers') {
    if (env.CHANGE_ID) {
      echo "PR detected"
      withCredentials([string(credentialsId: 'tokenGithub', variable: 'GITHUB_TOKEN')]) {
        sh "curl -s -H \"Authorization: token ${GITHUB_TOKEN}\" -X POST -d '{\"body\": \"Test comment from Jenkins\"}' \"https://api.github.com/repos/AnneRey/test-jenkins/issues/6/comments\""
      }
      //def comment = pullRequest.comment('Testing comment on befalf of Jenkins ;S ')
    }
  }
  
  stage ('Clean up') {
    cleanWs()
  }

}
