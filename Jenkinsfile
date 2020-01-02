 node ('master') {        
   checkout scm        
   stage('Build') {          
     withMaven(maven: 'M3') {
        if (isUnix()) {              
          sh 'mvn -Dmaven.test.failure.ignore clean package'            
        } else {              
          bat 'mvn -Dmaven.test.failure.ignore clean package'           
        }          
      }        
    }
    stage('Results') {          
       sh 'sleep 3600'
      junit '**/target/surefire-reports/TEST-*.xml'
      
      archive 'target/*.jar'        
    }      
  }
