pipeline{
    agent any
    stages{
        stage('Imprimir variables'){
                steps{
                    sh 'echo "HOLA"'
                    sh 'echo "QUE TAL"'
                    sh 'echo "ESTOY EN LA RAMA DESARROLLO"'
                }

        }

    }
    post{
        always{
            sh 'echo "FIN Jenkinsfile"'
        }
	
    }
}


