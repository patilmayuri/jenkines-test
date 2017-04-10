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
		if [foodcritic -V]; then
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
               println "Execution passed"
	       notifyBuild(currentBuild.result,"NULL")	      
	      
	      }
    catch(Exception e){
                 println "Execution failed"
	    	 notifyBuild("FAILED","${e}")
                 sh "exit 1"
             }
}  

def notifyBuild(String buildStatus = 'STARTED',String thiserr) {
  buildStatus =  buildStatus ?: 'SUCCESSFUL'
	
	def colorName = 'RED'
  	def colorCode = '#FF0000'
	
  if (buildStatus == 'STARTED') {
    color = 'YELLOW'
    colorCode = '#FFFF00'
  } else if (buildStatus == 'SUCCESSFUL') {
    color = 'GREEN'
    colorCode = '#00FF00'
	  step([$class: 'GitHubCommitStatusSetter',
        contextSource: [$class: 'ManuallyEnteredCommitContextSource',
        context: 'BUILD STATUS'],
        statusResultSource: [$class: 'ConditionalStatusResultSource',
        results: [[$class: 'AnyBuildResult',
        message: 'SUCCESSFUL',
        state: currentBuild.result]]]])
        echo "status set to ${buildStatus}."
	  
  } else if (buildStatus == 'FAILED') {
    color = 'RED'
    colorCode = '#FF0000'
	  step([$class: 'GitHubCommitStatusSetter',
        contextSource: [$class: 'ManuallyEnteredCommitContextSource',
        context: 'BUILD STATUS'],
        statusResultSource: [$class: 'ConditionalStatusResultSource',
        results: [[$class: 'AnyBuildResult',
        message: 'FAILED',
        state: '${buildStatus}']]]])
        echo "status set to ${buildStatus}."
	 
} 
	step([$class: 'WsCleanup', cleanWhenFailure: true])
}
