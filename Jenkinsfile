node {

	currentBuild.result = "SUCCESS"
	echo "initial file.........."
	try
            {
		stage('Checkout') {
		checkout scm
		}
		 
		stage('Test') {
		echo "Running: Test"
		sh '''set +x;
                 sudo gem install foodcritic;
		 foodcritic .;
                 rubocop .
		'''
		}
	    }

    catch(e)
        {
		echo e 
		throw e
	}
}
