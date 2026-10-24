
pipeline {
    agent any

    stages {
        stage('Restore') {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        success {
            echo 'Build and tests completed successfully!'
        }

        failure {
            echo 'Build or tests failed!'
        }
    }
}
