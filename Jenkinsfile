node {
	stage('Initialize'){
		env.NODEJS_HOME = "${tool 'NodeJS'}"
		env.PATH = "${env.NODEJS_HOME}/bin:${env.PATH}"
		sh 'pwd'
		sh 'yarn -v'
		checkout scm
		sh 'yarn install'
	}

  stage('test'){
    sh 'yarn test'
    
		publishHTML target: [
      allowMissing: false,
			alwaysLinkToLastBuild: false,
			keepAll: true,
			reportDir: 'coverage/lcov-report',
			reportFiles: 'index.html',
			reportName: 'RCov Report'
		]
  }
}

