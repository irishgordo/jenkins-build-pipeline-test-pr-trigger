pipeline{
  agent any
  parameters {
    booleanParam('notifier', false, 'will do notification things...')
  }
  triggers {
    githubPullRequest{
      admin('irishgordo')
      orgWhitelist('harvester')
    }
    issueCommentTrigger('^run-tests-*')
  }
  stages {
    stage('Build') {
        options {
          timeout(time: 10, unit: "MINUTES")
        }
        steps {
            script{
              sh "echo 'Building..'"
              def triggerCause = currentBuild.rawBuild.getCause(org.jenkinsci.plugins.pipeline.github.trigger.IssueCommentCause)
              sh "echo ${triggerCause.comment}"
            }
        }
    }
    stage('Test') {
        steps {
            echo 'Testing..'
        }
    }
    stage('Deploy') {
        steps {
            echo 'Deploying....'
        }
    }
  }
}
