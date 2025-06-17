pipeline {
    agent any

    environment {
        MY_NAME = 'Jenkins'
    }

    stages {
        stage('Say Hello') {
            steps {
                echo "Hello,${env.MY_NAME}!"
            }
        }

        stage('Git Information') {
            steps {
                script {
                    // Print branch name
                    def branch = sh(script: "git rev-parse --abbrev-ref HEAD", returnStdout: true).trim()
                    echo "Branch Name: ${branch}"

                    // Print latest commit hash
                    def commit = sh(script: "git rev-parse HEAD", returnStdout: true).trim()
                    echo "Latest Commit: ${commit}"
                }
            }
        }

        stage('Unit Tests') {
            steps {
                echo 'Running Unit Tests...'
                sh 'echo "Tests passed!"'
            }
        }

        stage('build') {
            steps {
                echo 'Building the project...'
                sh 'echo "Build completed!"'
            }
        }

        stage('deploy') {
            steps {
                echo 'Deploying the project...'
                sh 'echo "Deployment complete!"'
            }
        }

        stage('Running on Ubuntu') {
            steps {
                echo 'Running tests on Ubuntu...'
            }
        }

        stage('Promote to Green') {
            steps {
                echo 'Promoting to Green Environment...'
            }
        }

        stage('Promote Development Branch to Master') {
            steps {
                echo "Merging development into master..."
                sh '''
                    git checkout master
                    git fetch origin development:development
                    git merge development
                '''
            }
        }
    }

    post {
        always {
            emailext (
                to: 'pkarthickraja9@gmail.com',
                subject: "Job '${env.JOB_NAME}' (#${env.BUILD_NUMBER})",
                body: "Build completed. View at: ${env.BUILD_URL}"
            )
        }
    }
}
