pipeline {
    agent any

    environment {
        GITHUB_TOKEN = credentials('github')  // use the credential ID you created
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Archive git.html') {
            steps {
                echo "Archiving git.html"
                archiveArtifacts artifacts: 'git.html', fingerprint: true
            }
        }

        stage('Use Secret Token Example') {
            steps {
                // Example: show you can use the token in an operation
                echo "Using GitHub token (masked): ${GITHUB_TOKEN}"
                
                // If you needed to call GitHub API, you could do:
                // sh "curl -H \"Authorization: token ${GITHUB_TOKEN}\" https://api.github.com/…"
            }
        }
    }

    post {
        success {
            echo "Pipeline succeeded."
        }
        failure {
            echo "Pipeline failed."
        }
    }
}
