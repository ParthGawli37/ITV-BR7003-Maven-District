pipeline {
    agent any
    
    triggers {
		parameterizedCron(
			'58 15 * * * % BROWSER=chrome;ENVIRONMENT=qa'
			'60 15 * * * % BROWSER=firefox;ENVIRONMENT=uat'
			'02 15 * * * % BROWSER=edge;ENVIRONMENT=prod'
			
			)
	
	}
    
    
    parameters {
		choice(
			name: 'BROWSER',
			choices: ['chrome', 'edge', 'firefox'],
            description: 'Select the browser to run tests on'
		)
		choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'qa', 'prod'],
            description: 'Select the environment to run tests on'
        )
	}

    tools {
        jdk 'Java_JDK'
        maven 'MAVEN'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/nextgentestingacademy/ITV-Maven-Batch703.git',
                    branch: 'main'
            }
        }

        stage('Build & Test') {
            steps {
                bat "mvn clean test -Dbrowser=${params.BROWSER} -Denvironment=${params.ENVIRONMENT}"
            }
        }
    }
}