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
            agent any

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
                // Simulate test
                sh 'echo "Tests passed!"'
            }
        }

        stage('build') {
            steps {
                echo 'Building the project...'
                // Simulate build
                sh 'echo "Build completed!"'
            }
        }

        stage('deploy') {
            steps {
                echo 'Deploying the project...'
                // Simulate deploy
                sh 'echo "Deployment complete!"'
            }
        }

        stage('Running on Ubuntu') {
            agent any
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
                echo 'Merging development into master...'
                sh '''
                git checkout master
                git merge development
                '''
            }
        }
    }

    post {
        always {
            emailext (
                to: 'pkarthickraja9@gmail.com',
                subject: "Job '${env.JOB_NAME}' (${env.BUILD_NUMBER})",
                body: "Build completed: ${env.BUILD_URL}"
            )
        }
    }
}
