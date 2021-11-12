pipeline{
		agent any
				stages{
				       stage('one'){
								steps{
									echo 'Hi jenkins'
								}
					   }
					   stage('two'){
								steps{
								input('Proceed..?')
								}
					   }
				}
}
