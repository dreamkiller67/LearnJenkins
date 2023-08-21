pipeline{
		agent {label 'master'}
				stages{
				       stage('one'){
								steps{
									echo 'welcome to jenkins baba'
								}
					   }
					   stage('build'){
								steps{
								sh 'mvn --version'
								}
					   }
				}
}
