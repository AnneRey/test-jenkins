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
      def comment = pullRequest.comment('Testing comment on befalf of Jenkins ;S ')
    }
  }
  
  stage ('Clean up') {
    cleanWs()
  }

}
