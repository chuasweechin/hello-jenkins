pipeline {
  agent any
  
  environment {
    APP_VERSION = '1.0.0'
  }
  
  parameters {
    choice(name: 'APP', choices: ['frontend', 'backend'], description: '')
    booleanParam(name: 'executeTests', defaultValue: false, description: '')
  }
  
  stages {
    stage('build') {
      steps {
        echo "building ${params.APP}...."
        echo "building version ${APP_VERSION}...."        
      }
    }
    
    stage('test') {
      when {
        expression {
          params.executeTests
        }
      }
      
      steps {
        echo "test ${params.APP}...."
      }
    }
    
    stage('deploy') {
      when {
        expression {
          BRANCH_NAME == 'main'
        }
      }
      
      steps {
        echo "deploy ${params.APP}...."
        
        withCredentials([
          usernamePassword(credentialsId: 'github_account', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')
        ]) {
          echo "some script ${USERNAME}...."
        }
      }
    }
  }
}
