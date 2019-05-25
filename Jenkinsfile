pipeline{
   agent { docker 'maven:3.5-alpine'}
   stages {
      stage('checkout'){
        steps{
        git 'https://github.com/KAZAMA7/spring-petclinic.git'
           }
         }
        stage('build'){
           steps{
              sh 'mvn clean package'
              junit '**/target/surefire-reports/TEST-*.xml'
              archiveArtifacts artifacts: 'target/*.jar', fingerprint: true, onlyIfSuccessful: true
           }
         }
      }
   }
