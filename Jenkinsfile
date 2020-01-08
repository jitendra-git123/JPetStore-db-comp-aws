node {
        def majorVersion="2.0.${BUILD_NUMBER}"
	currentBuild.displayName = majorVersion

	//currentBuild.displayName = "4.0.${BUILD_NUMBER}"
	def GIT_COMMIT
  stage ('cloning the repository'){
	  
      def scm = git 'https://github.com/jitendra-git123/Jpetstore-db-comp'
	  GIT_COMMIT = sh(returnStdout: true, script: "git rev-parse HEAD").trim()
	  echo "COMMITID ${GIT_COMMIT}"
	  //echo "BBBB ${scm}"
	  //GIT_COMMIT = scm.GIT_COMMIT
	   //echo "**** ${GIT_COMMIT}"
	  
  }
	
 
  

	
echo "(*******)"	
  stage('Publish Artificats to UCD'){
	  
   step([$class: 'UCDeployPublisher',
	        siteName: 'UCD_Local',
	        component: [
	            $class: 'com.urbancode.jenkins.plugins.ucdeploy.VersionHelper$VersionBlock',
	            componentName: 'JPetStoreUOB-db-Component',
	            createComponent: [
	                $class: 'com.urbancode.jenkins.plugins.ucdeploy.ComponentHelper$CreateComponentBlock',
	                componentTemplate: '',
	                componentApplication: 'JPetStore-UOB'
	            ],
	            delivery: [
	                $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeliveryHelper$Push',
	                pushVersion: '2.0.${BUILD_NUMBER}',
	                //baseDir: '/var/jenkins_home/workspace/JPetStore/target',
			 baseDir: 'D:/Installables/Jenkins/workspace/UOB/JPetStore-db/src/database/',
	                fileIncludePatterns: '**/*.sql',
	                fileExcludePatterns: '',
	               // pushProperties: 'jenkins.server=Jenkins-app\njenkins.reviewed=false',
	                pushDescription: 'Pushed from Jenkins'
	            ]
	        ]
     ])
	  
		//sh 'env > env.txt'
	//	readFile('env.txt').split("\r?\n").each {
	//	println it
	//	}
//	echo "(*******)"
//	  echo "Demo1234 ${JPetStorevelocityComponent_VersionId}"
//	  def newComponentVersionId = "${JPetStorevelocityComponent_VersionId}"
//	  echo "git commit ${GIT_COMMIT}"
//	  //step($class: 'UploadBuild', tenantId: "5ade13625558f2c6688d15ce", revision: "${GIT_COMMIT}", appName: "Altoro", requestor: "admin", id: "${newComponentVersionId}" )
// step($class: 'UploadBuild', 
  //     tenantId: "5ade13625558f2c6688d15ce", 
    //   revision: "${GIT_COMMIT}", 
      // appName: "JPetStore-velocity", 
    //   requestor: "admin", 
   //    id: "${newComponentVersionId}", 
   //    versionName: "3.0.${BUILD_NUMBER}"
   //   )
     
//	//echo "Demo123 ${newComponentVersionId}"
//	//sleep 25
//	  step([$class: 'UCDeployPublisher',
//		deploy: [ createSnapshot: [deployWithSnapshot: true, 
//			 snapshotName: "2.0.${BUILD_NUMBER}"],
//			 deployApp: 'JPetStore-velocity', 
//			 deployDesc: 'Requested from Jenkins', 
//			 deployEnv: 'JPetStore-velocity_Dev', 
//			 deployOnlyChanged: false, 
//			 deployProc: 'Deploy-JPetStore-velocity', 
//			 deployReqProps: '', 
//			 deployVersions: "JPetStorevelocityComponent:2.0.${BUILD_NUMBER}"], 
//		siteName: 'UCD_Local'])

 }
	
stage ('wait for deploy') {
	sleep 25
	// echo 'Executing HCL One test ... '
	//sh '/var/jenkins_home/onetest/hcl-onetest-command.sh'
 }	

}

