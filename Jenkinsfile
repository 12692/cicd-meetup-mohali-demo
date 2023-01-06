pipeline {
  agent any
  stages {
    stage('Build Application') { 
      steps {
        bat 'mvn clean install'
      }
    }
 	stage('Test') { 
      steps {
        echo 'Test Appplication...' 
        bat 'mvn test'
      }
    }
 	
    stage('Deploy CloudHub') { 
    	      environment {
        ANYPOINT_CREDENTIALS = credentials('mulesoft.meetup')
      }
       steps {
        echo 'Deploying only because of code commit...'
        bat 'mvn package deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -Denvironment=Sandbox -DworkerType=Micro -Dworkers=1 -Dregion=us-west-2'
      }
    }
  }
}
