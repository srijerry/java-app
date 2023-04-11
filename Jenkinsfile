pipeline{

    agent any

    stages{

        stage('Git checkout'){

            steps{

                script{
                gitCheckout(
                    branch: "main"
                    url: "https://github.com/srijerry/java-app.git"
                }
            }
        }
    }
}            