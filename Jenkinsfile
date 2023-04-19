pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Hello World from build'
                git branch: 'main', credentialsId: '', url: 'https://github.com/YuriiOnufreiv/test'
                // sh 'mkdir -p data/elasticsearch'
                // sh 'chmod 777 data/elasticsearch'
                // sh 'docker compose -p reportportal up -d'
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
