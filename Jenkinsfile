pipeline{
   agent any
   stages {
      stage('checkout'){
        steps{
        git 'https://github.com/KAZAMA7/spring-petclinic.git'
           }
         }
        stage('build'){
           agent { docker 'maven:3.5-alpine'}
           steps{
              sh 'mvn clean package'
              junit '**/target/surefire-reports/TEST-*.xml'
              archiveArtifacts artifacts: 'target/*.jar', fingerprint: true, onlyIfSuccessful: true
           }
         }
         stage('deploying application'){
           steps{
             sh 'scp target/*.jar slave1:/tmp/petclinic/'
             sh 'ssh slave1 "nohup java -jar /tmp/petclinic/*.jar &"'
             }
           }
      }
   }
