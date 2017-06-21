node {
  stage("Git Checkout") {
    checkout(scm)
  }
  stage("Git Tag") {
    sh "pwd"
    sh "ls -la"
    withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'github-token', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME']]) {
      sh('git tag -a $(date "+%s") -m "Jenkins"')
      sh('git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/TYPO3-cookbooks-test/credentials --tags')
    }
  }
}
