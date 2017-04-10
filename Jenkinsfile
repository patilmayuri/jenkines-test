pipeline {

	echo "initial file.........."
	try
            {
		stage('Checkout') {
		checkout scm
		}

    catch(e)
        {
		echo e 
		throw e
	}
	
 }
}
