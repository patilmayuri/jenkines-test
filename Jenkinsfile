node {

	echo "initial file.........."
	try
            {
		stage('Checkout') {
		checkout scm
		}
		 
		stage('Test') {
		echo "Running: Test"
		sh '''set +x;
		 foodcritic .
		'''
		}
	    }

    catch(e)
        {
		echo e 
		throw e
	}
	
}

