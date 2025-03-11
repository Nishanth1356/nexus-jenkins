pipelinbe{
    stages{
        stage('validate') {
            steps {
                sh 'mvn validate'
            }
        }

          stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('store artifact into nexus') {
            steps {
                sh 'mvn -s settings.xml clean deploy'
            }
            post{
                success{
                    echo 'artifact stored successfully'
                }
                failure{
                    echo 'failed to staore'
                }
            }
        }
    }

    post{
        always{
            echo 'always executing'
        }
        success {
            echo 'build completedsuccessfully'
        }
        failure{
            echo 'build failed! check logs for details'
        }
    }
}
