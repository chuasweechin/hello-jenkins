pipeline {
  agent any
  
  stages {
    stage("build") {
      steps {
        echo "building app...."
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
