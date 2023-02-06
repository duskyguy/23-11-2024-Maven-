pipeline {
    agent any
    tools {
        maven "maven_3"
    }
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'git@github.com:kmayer10/maven-sample-project.git'
                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    archiveArtifacts 'target/devops.war'
                }
            }
        }
    }
}
