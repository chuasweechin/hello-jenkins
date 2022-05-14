pipeline {
  agent any
  
  environment {
    APP_VERSION = "1.0.0"
  }
  
  stages {
    stage("build") {
      steps {
        echo "building app...."
        echo "building version ${APP_VERSION}...."
      }
    }
    
    stage("test") {
      steps {
        echo "test app...."
      }
    }
    
    stage("deploy") {
      when {
        expression {
          BRANCH_NAME == 'deploy'
        }
      }
      steps {
        echo "deploy app...."
      }
    }
  }
}
