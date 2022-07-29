pipeline {
    
    agent any
    parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'main', name: 'BRANCH', type: 'PT_BRANCH'
    }

    options {
        timestamps ()
    }

    stages {

        stage('Checkout Stage') {
            steps {
                git branch: "${params.BRANCH}",
                url: 'https://github.com/ochirkov/cicd-sessions-repo.git'
            }
        }

        stage('Parallel Execution') {
            parallel {
                stage('Docs Stage') {
                    steps {
                        echo "it is docs stage"
                        //sh "tox -e docs"
                    }
                }

                stage('Linters Stage') {
                    steps {
                        echo "it is linters stage"
                        //sh "tox -e linters"
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}