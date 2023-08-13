pipeline{
		agent {docker { image 'maven:3.9.3-eclipse-temurin-17-alpine' }}
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
