pipeline{
	agent any
	environment{
	 LANG='en_US.UTF-8'
	 LC_ALL='en_US.UTF8'}
	 tools{
	 maven 'Maven'}
	 stages{
	 	stage('Checkout'){
	 		steps{ git branch: 'master' , url: 'https://github.com/fluffy-panda07/MavenAnsible.git'}}
	 	stage('Build'){
	 		steps{ sh 'mvn clean package'}}
	 	stage('Test'){
	 		steps{ sh 'mvn test'}}
	 	stage('Archive'){
	 		steps{ archiveArtifacts artifacts:'target/*.war',fingerprint:true}}
	 	stage('Deploy'){
	 		steps{ sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini' }}
	 	}
	 post{
	 	success{ echo 'Build and deployment succesfull}
	 	failure{ echo 'build failed'}
	 	}
	 	}
	 
