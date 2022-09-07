pipeline {
    agent any

    parameters {
	booleanParam(name: "RUN_INTEGRATION_TESTS", defaultValue: true
    }

    stages {
        stage('test') {
	    parallel {
                stage('unit tests') {
 		    steps {
 			sh './mvnw test -D testGroups=unit'
                    }
		}
		stage('int tests') {
 		   when {
		       expression { return params.RUN_INTEGRATION_TEST }
		   }
		   steps {
		       sh './mvnw test -D testGroups=integration'
		   }   
                }
            } 
        }
    }
}
