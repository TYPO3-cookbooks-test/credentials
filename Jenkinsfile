node {
  stage("Git") {
    withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'github-token', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME']]) {
      sh('git tag -a $(date "+%s") -m "Jenkins"')
      sh('git push https://${GIT_USERNAME}:${GIT_PASSWORD}@https://github.com/TYPO3-cookbooks-test/credentials --tags')
    }
  }
}
