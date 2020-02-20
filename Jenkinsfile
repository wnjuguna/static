pipeline {
	agent any
	stages {
		stage('Build') {
			steps{
				sh 'echo "Hello World"'
				sh '''
					echo "Multiline shell steps work too"
					ls -alh
				'''
			}
		}
		stage('Upload to AWS'){
			steps{
				withAWS(region:'us-west-2',credentials:'aws-static') {
					s3Upload(file:'src/index.html', bucket:'udacity-ci', path:'index.html')
				}
			}
		}
	}
}
