@Library('my-shared-library') _

pipeline{

    agent any

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'choose create/destroy')
    }

    stages{

        when { expression  { param.action == 'create' } }

        stage('Git checkout'){

            steps{

                script{
                gitCheckout(
                    branch: "main",
                    url: "https://github.com/srijerry/java-app.git"
                )
                }
            }
        }
        stage('unit test maven'){

        when { expression  { param.action == 'create' } }
            
            steps{

                script{

                    mvntest()

                }
            }
        }
        stage('intergartion test maven'){

        when { expression  { param.action == 'create' } }
            
            steps{

                script{

                    mavenintegrationtest()

                }
            }
        }
        stage('static code analysis'){

        when { expression  { param.action == 'create' } }
            
            steps{

                script{

                    staticcodeanalysis()

                }
            }
        }
    }
}            