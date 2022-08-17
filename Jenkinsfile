pipeline{
  agent any
  environment {
    TRIGGER_CAUSE = currentBuild.rawBuild.getCause(org.jenkinsci.plugins.pipeline.github.trigger.IssueCommentCause)
  }
  stages {
    stage('Build') {
        options {
          timeout(time: 10, unit: "MINUTES")
        }
        steps {
          script{
              sh 'printenv' 
              params.each {param ->
                println "${param.key} -> ${param.value} "
              }
              sh "echo 'Building..'"
              sh 'echo "${TRIGGER_CAUSE.comment}"'
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
