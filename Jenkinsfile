pipeline {
 	agent any
 	stages {
 		stage('Build') { 
			steps {
 				sh 'mvn -B -DskipTests clean package' 
			}
 		}
		stage('Doc') {
			steps {
				sh 'mvn javadoc:jar'
			}
		}
 		stage('pmd') {
 			steps {
 				sh 'mvn pmd:pmd'
 			}
 		}
		stage('Test report') {
			steps {
				sh 'mvn test --fail-never'
				sh 'mvn surefire-report:report'
			}
		}
 	}
	
 	post {
 		always {
 			archiveArtifacts artifacts: 'docs-core/target/docs-core-1.10-javadoc.jar', fingerprint: true
 			archiveArtifacts artifacts: 'docs-core/target/docs-core-1.10.jar', fingerprint: true
 			archiveArtifacts artifacts: 'docs-web/target/docs-web-1.10-javadoc.jar', fingerprint: true
            archiveArtifacts artifacts: 'docs-web/target/docs-web-1.10.war', fingerprint: true
            archiveArtifacts artifacts: 'docs-web-common/target/docs-web-common-1.10-javadoc.jar', fingerprint: true
            archiveArtifacts artifacts: 'docs-web-common/target/docs-web-common-1.10-tests.jar', fingerprint: true
            archiveArtifacts artifacts: 'docs-web-common/target/docs-web-common-1.10.jar', fingerprint: true
            archiveArtifacts artifacts: 'docs-web-common/target/docs-web-common-1.10.jar', fingerprint: true
 			archiveArtifacts artifacts: '**/target/site/pmd.html', fingerprint: true
 			archiveArtifacts artifacts: '**/target/site/surefire-report.html', fingerprint: true
 		}
 	}
 }
