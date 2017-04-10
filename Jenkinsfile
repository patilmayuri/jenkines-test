node {
  currentBuild.result = "SUCCESS"
	echo "initial file.........."
	try
              {
		stage('Checkout') {
		checkout scm
		}

		stage('Checkout and build deps') {
		sh '''
		sudo gem install rubocop
		if [foodcritic -V]
		sudo gem install foodcritic
		fi	
		'''
		}
		stage('Test') {
		echo "Running: Test"
		sh '''set +x;	
		foodcritic .; 
		rubocop .
		'''
		}
	  }
    catch(Exception e){
                 println "Execution failed"
                 sh "exit 1"
             }
             println "Execution passed"
}
