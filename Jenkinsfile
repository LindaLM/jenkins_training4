pipeline {

    agent any

    parameters {
        gitParameter branchFilter: 'origin/(.*)', defaultValue: 'main', name: 'BRANCH', type: 'PT_BRANCH'
    }

    stages {

        stage('Checkout Stage') {
            steps {
                git branch: "${params.BRANCH}", 
                url: 'https://github.com/LindaLM/jenkins_training4.git'
            }
        }

        stage('Parallel Execution') {
            parallel {
                stage('Docs Stage') {
                    steps {
                        echo "it is docs stage"
                        sh "tox -e docs"
                    }
                }

                stage('Linters Stage') {
                    steps {
                        echo "IT'S LINTER STAGE"
                        //sh "tox -e linters"
                    }
                }

                stage('Linters Stage') {
                    steps {
                        echo "IT'S COVER STAGE"
                        sh "tox -e cover"
                    }
                }
            }
        }
    }
}