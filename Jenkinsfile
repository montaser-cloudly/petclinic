pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stage('Compile') {
       steps {
         sh 'mvn compile' //only compilation of the code
       }
    }


    stage('Test') {
      steps {
        echo 'Testing...'
        snykSecurity(
          snykInstallation: 'petclinic-test',
          snykTokenId: 'petclinic-snyk',
          // place other parameters here
        )
      }
    }
}



    
//    stages {
//       stage('Build') {
//           steps {
//               sh 'gradle assemble'
//           }
//       }
//        stage('Test') {
//           steps {
//               sh 'gradle test'
//           }
//       }
//       stage('Build Docker Image') {
//           steps {
//               sh 'gradle docker'
//           }
//       }
//       stage('Run Docker Image') {
//           steps {
//               sh 'gradle dockerRun'
//           }
//       }
//   }



