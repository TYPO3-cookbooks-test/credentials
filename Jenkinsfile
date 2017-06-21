node {
  stage("Git Checkout") {
    checkout(scm)
  }
  stage("Git Tag") {
    sh "pwd"
    sh "ls -la"
    withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'github-token', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME']]) {
      sh('git tag -a $(date "+%s") -m "Jenkins"')
      //sh "echo 'protocol=https\nhost=github.com\nusername=${GIT_USERNAME}\npassword=${GIT_PASSWORD}\n\n' | git credential approve "
      giturl_push = GIT_URL.split("//")[1]
      sh("git push https://${env.GIT_USERNAME}:${env.GIT_PASSWORD}@${giturl_push} --tags")
    }
  }
}
