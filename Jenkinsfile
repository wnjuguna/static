pipeline {
	agent any
	stages {
		stage('Lint HTML') {
			steps{
				sh '''
					tidy -qe src/html/*
				'''
			}
		}
		stage('Upload to AWS'){
			steps{
				withAWS(region:'us-west-2',credentials:'aws-static') {
					s3Upload(file:'src/html/index.html', bucket:'udacity-ci', path:'index.html')
				}
			}
		}
	}
}
