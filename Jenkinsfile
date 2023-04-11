@Library('my-shared-library') _

pipeline{

    agent any

    stages{

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

            steps{

                script{

                    mvntest()

                }
            }
        }
        stage('intergartion test maven'){

            steps{

                script{

                    mavenintegrationtest()

                }
            }
        }
    }
}            