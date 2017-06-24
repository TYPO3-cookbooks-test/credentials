node {
  stage("Git Checkout") {
    checkout(scm)
  }
  stage("Git Tag") {
    sh "pwd"
    sh "ls -la"
    withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'github-token', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME']]) {
      sh('git tag -a $(date "+%s") -m "Jenkins"')

//      def gitUrl = sh(script: "git remote get-url origin", returnStdout: true)
//      gitCredentialsUrl = gitUrl.replace('://', '://' + env.GIT_USERNAME + ':' + env.GIT_PASSWORD')
                                         
//      sh("git config credential.username ${env.GIT_USERNAME}")
//      sh("git config credential.helper '!echo password=\$GIT_PASSWORD; echo'")
//      sh("GIT_ASKPASS=true git push origin --tags")
      
      gitCredentialsUrl = scm.getUserRemoteConfigs()[0].getUrl().replace('://', '://' + env.GIT_USERNAME + ':' + env.GIT_PASSWORD + '@')
//      gitCredentialsUrl = gitCredentialsUrl.replace('.git', '')
      command = "git push ${gitCredentialsUrl} --tags"
      writeFile(file: 'command.sh', text: command)
      sh(command)
    }
  }
}
