// Powered by Infostretch 

timestamps {

node () {

	stage ('hellowhale - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '0756a45d-5e41-435c-a66c-00a2e0e8fa13', url: 'https://github.com/cmurad0215/DotNetCoreRazor.git']]]) 
	}
	stage ('hellowhale - Build') {
 			// Shell build step
sh """ 
IMAGE_NAME="cmurad0215z/hellowhale:${BUILD_NUMBER}"
docker build . -t $IMAGE_NAME
docker login -u cmurad0215z -p ${DOCKER_HUB}
docker push $IMAGE_NAME 
 """		// Shell build step
sh """ 
IMAGE_NAME="cmurad0215z/hellowhale:${BUILD_NUMBER}"
kubectl set image -n default deployment/hellowhale hellowhale=$IMAGE_NAME 
 """ 
	}
}
}