pipeline {
  agent {label "linux"}
  tools {
        maven 'maven3.8.1'
        jdk 'jdk1.8'
    }
  stages{
    stage('BUILD: prepare environment'){ 
      when {
        anyOf { branch 'develop'; branch 'main' }
      }
      steps {
        echo 'prepare Maven, Java JDK'
        sh  """
              mvn --version
              java -version
            """
      }
    }
    stage('DEPLOY: develop'){
      when {
        branch 'develop'
      }
      steps {
          sh 'chmod +x /Users/khoahoang/.jenkins/demoproject/uat_script.sh'
          sh '/Users/khoahoang/.jenkins/demoproject/uat_script.sh'
        }
    }
    stage('DEPLOY: main'){
      when {
        branch 'main'
      }
      steps {
          sh 'chmod +x /Users/khoahoang/.jenkins/demoproject/prod_script.sh'
          sh '/Users/khoahoang/.jenkins/demoproject/prod_script.sh'
      }
    }
  }
}
