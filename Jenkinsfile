pipeline {
    try
        {
		stage('Checkout') {
		checkout scm
		}

                
		stage('Build_Backend_Code') {
		echo "Running: Build_Backend_Code"
		sh '''set +x;
		 mvn clean install
		'''
		}

        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }

    catch(e)
        {
		echo e 
		throw e
	}
			
}
