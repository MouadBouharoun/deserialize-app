pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
          echo "PATH = ${PATH}"
          echo "M2_HOME = ${M2_HOME}"
        ''' 
      }
    } 

    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy to Tomcat') {
      steps {
        sh 'sshpass -p "jenkins" scp -o StrictHostKeyChecking=no target/*.jar mouad@192.168.26.135:/home/mouad/Desktop/apache-tomcat-9.0.80/webapps'
      }
    }
  
    
    }  

}
