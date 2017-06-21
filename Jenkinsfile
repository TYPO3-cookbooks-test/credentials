node {
  stage("Git Checkout") {
    checkout(scm)
  }
  stage("Git Tag") {
    sh "pwd"
    sh "ls -la"
    withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'github-token', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME']]) {
      sh('git tag -a $(date "+%s") -m "Jenkins"')

      sh("git config credential.username ${env.GIT_USERNAME}")
      sh("git config credential.helper '!echo password=\$GIT_PASSWORD; echo'")
      sh("GIT_ASKPASS=true git push origin --tags")
      
      // giturl_push = scm.getUserRemoteConfigs()[0].getUrl().split("//")[1]
      // sh("git push https://${env.GIT_USERNAME}:${env.GIT_PASSWORD}@${giturl_push} --tags")
    }
  }
}
