/*
    Este pipeline es la plantilla minima que deberian de tener para su proyecto
    de clase 
*/
pipeline{
    agent any
	
    stages{
        
		stage('Build'){
            /*
                Aqui tienen que tener todos los pasos necesarios para
                construir la aplicacion
                Ejemplos:
                - nodejs -> construccion con gulp o npm
                - java -> construccion con maven o gradle
                - .net -> MSBuild 
            */
			steps{
				sh 'npm install'
				sh 'echo termino la verificacion de dependencias'
			}

		}
        stage('Pruebas-Unitarias'){
            /*
                Aqui se ejecutaran las pruebas unitarias segun su framework de pruebas
                y su lenguaje de programacion 
            */
            steps{
                sh 'npm test'
            }
        }
		stage(' Pruebas staticas Sonarqube') {
			environment {
				scannerHome = tool 'SonarQubeScanner'
			}
			steps {
				sh 'echo "con gate de coverage y arrojaria error???"'
				sh 'echo $scannerHome'
                /*modificar el token y la IP*/
				withSonarQubeEnv('sonarqube') {
            		sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=ayd2 \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://35.184.187.153:5001 \
                    -Dsonar.login=843506c8d44155471da1d9a524475a456b8ebb16"
        		}
				timeout(time: 1, unit: 'MINUTES') {
            		waitForQualityGate abortPipeline: true
        		}		
			}
        }
        /*
        este stage no se las calificare en la siguiente revision de midsprint
        */
        stage('Pruebas de integracion'){
            steps{
                sh 'echo "levantar lo necesario para las pruebas de integracion"'
                sh 'echo "voy a ejecutar un scrip de selenium"'
            }
        }
        /*
        este stage no se las calificare en la siguiente revision de midsprint
        */
        stage('Deploy'){
            steps{
                sh 'echo "aqui podran utilizar Ansible o otra herramienta junto con docker."'
            }
        }

    }
    post{
	    always{
	    	sh 'echo "FIN"'
	    }
	
    }
}