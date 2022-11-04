pipeline {
  agent {label "linux"}
  tools {
        maven 'maven3.8.1'
        jdk 'jdk1.8'
    }
  stages{
    stage('hello') {
      steps {
        echo 'hello from Jenkinsfile'
      }
    }
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
        sh 'mvn clean deploy -DmuleDeploy -DskipTests -Dmule.version=4.4.0 -Danypoint.username=khoamule8 -Danypoint.password=123456Aaq -Denv=Sandbox -Dbusiness=Tiki -DvCore=Micro -Dworkers=1'
      }
    }
    stage('DEPLOY: main'){
      when {
        branch 'main'
      }
      steps {
        sh 'mvn clean deploy -DmuleDeploy -DskipTests -Dmule.version=4.4.0 -Danypoint.username=khoamule7 -Danypoint.password=123456Aa@ -Denv=Sandbox -Dbusiness=Tiki -DvCore=Micro -Dworkers=1'
      }
    }
  }
}
