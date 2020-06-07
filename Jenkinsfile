pipeline {
	agent any
	stages {
		stage('Compile Stage'){
			steps {
				withMaven(maven: 'maven_3_6_2'){
					sh 'man clean compile'
				}
			}
			
		}
		stage('Testing Stage'){
			steps {
				withMaven(maven: 'maven_3_6_2'){
					sh 'man test'
				}
			}
			
		}
		stage('Development Stage'){
			steps {
				withMaven(maven: 'maven_3_6_2'){
					sh 'man deploy'
				}
			}
			
		}
	}
}