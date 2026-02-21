pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage("Restore dependencies") {
            when {
                branch 'main'
            }
            steps {
                bat 'dotnet restore'
            }
        }

        stage("Build the app") {
            when {
                branch 'main'
            }
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage("Run the tests") {
            when {
                branch 'main'
            }
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        success {
            echo "Build and tests succeeded on main branch!"
        }
        failure {
            echo "Build or tests failed on main branch!"
        }
    }
}