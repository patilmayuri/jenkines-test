node {

	currentBuild.result = "SUCCESS"

    try {

        stage ('Checkout') {

            checkout scm
            sh """
                eval "\$(chef shell-init bash)"
                gem list --local
                gem install foodcritic
                gem install bundler
            """
        }

            }
            catch (Exception err) {
                currentBuild.result = "UNSTABLE"
            }
	
}
