void setBuildStatus(String message, String state) {
  step([
      $class: "GitHubCommitStatusSetter",
      reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/YuriiOnufreiv/test"],
      contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "ci/jenkins/build-status"],
      errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
      statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
  ]);
}

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Hello World from build'
//                 git branch: 'main', credentialsId: '', url: 'https://github.com/YuriiOnufreiv/test'
                // sh 'mkdir -p data/elasticsearch'
                // sh 'chmod 777 data/elasticsearch'
                // sh 'docker compose -p reportportal up -d'
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
                step([$class: 'GitHubCommitStatusSetter', statusResultSource: [$class: 'ConditionalStatusResultSource', results: []]])
            }
        }
    }
    
  post {
    success {
        setBuildStatus("Build succeeded", "SUCCESS");
    }
    failure {
        setBuildStatus("Build failed", "FAILURE");
    }
  }
}
