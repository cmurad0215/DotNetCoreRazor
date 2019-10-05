// Powered by Infostretch 

timestamps {

node () {

	stage ('hellowhale - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '0756a45d-5e41-435c-a66c-00a2e0e8fa13', url: 'https://github.com/cmurad0215/DotNetCoreRazor.git']]]) 
	}
	stage ('hellowhale - Build') {
 			// Shell build step
		bash ''' #!/bin/bash
			IMAGE_NAME="cmurad0215z/hellowhale:${BUILD_NUMBER}"
			docker build . -t $IMAGE_NAME
			docker tag hellowhale 172.31.24.185:5000/cmurad0215z/hellowhale:${BUILD_NUMBER}
			docker login 172.31.24.185:5000 -u murad -p 123
			docker push 172.31.24.185:5000/$IMAGE_NAME
 		'''		// Shell build step
		bash ''' #!/bin/bash
			IMAGE_NAME="cmurad0215z/hellowhale:${BUILD_NUMBER}"
			kubectl set image -n default deployment/hellowhale hellowhale=$IMAGE_NAME 
 		''' 
	}
}
}
