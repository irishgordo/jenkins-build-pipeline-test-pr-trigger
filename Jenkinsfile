pipeline{
  agent any
  triggers {
    issueCommentTrigger('.run-tests-*')
  }
  stages {
    stage('Build') {
        steps {
            echo 'Building..'
            script{
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
