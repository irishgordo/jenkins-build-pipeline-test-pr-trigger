pipeline{
  agent any
  environment {
    TRIGGER_CAUSE = currentBuild.rawBuild.getCause(org.jenkinsci.plugins.pipeline.github.trigger.IssueCommentCause)
  }
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
            sh 'printenv' 
            params.each {param ->
              println "${param.key} -> ${param.value} "
            }
            echo 'Building..'
            echo "${TRIGGER_CAUSE.comment}"
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
