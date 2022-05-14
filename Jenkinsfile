pipeline {
  agent any
  
  environment {
    APP_VERSION = "1.0.0"
  }
  
  parameters {
    string(name: "APP", choices: ["frontend", "backend"], defaultValue: "frontend", description: "")
    booleanParam(name: 'executeTests', defaultValue: false, description: "")
  }
  
  stages {
    stage("build") {
      steps {
        echo "building app...."
        echo "building version ${APP_VERSION}...."        
      }
    }
    
    stage("test") {
      when {
        expression {
          params.executeTests
        }
      }
      
      steps {
        echo "test app...."
      }
    }
    
    stage("deploy") {
      when {
        expression {
          BRANCH_NAME == 'main'
        }
      }
      
      steps {
        echo "deploy app...."
        
        withCredentials([
          usernamePassword(credentials: "github-account", usernameVariable: USERNAME, passwordVariable: PASSWORD)
        ]) {
          sh "some script ${USERNAME}"
        }
      }
    }
  }
}
