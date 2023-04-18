@Library('my-shared-library') _

pipeline{

    agent any

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'choose create/destroy')
    }

    stages{

        stage('Git checkout'){

        when { expression  {  params.action == 'create' } }

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

        when { expression  { params.action == 'create' } }
            
            steps{

                script{

                    mvntest()

                }
            }
        }
        stage('intergartion test maven'){

        when { expression  { params.action == 'create' } }
            
            steps{

                script{

                    mavenintegrationtest()

                }
            }
        }
        stage('static code analysis'){

        when { expression  { params.action == 'create' } }
            
            steps{

                script{
                    
                    def SonarQubecredentialsId = 'sonar-api'
                    staticcodeanalysis(SonarQubecredentialsId)

                }
            }
        }
        stage('QualityCheckStatus : soanr'){

        when { expression  { params.action == 'create' } }
            
            steps{

                script{
                    
                    def SonarQubecredentialsId = 'sonar-api'
                    QualityCheckStatus(SonarQubecredentialsId)

                }
            }
        }
        stage('maven Build'){

        when { expression  { params.action == 'create' } }
            
            steps{

                script{

                    mvnBuild()

                }
            }
        }
    }
}            