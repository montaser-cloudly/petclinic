pipeline {
    agent any
    tools{
        jdk 'jdk-18'
        maven '3.9.1'
    }
    
    triggers {
        pollSCM '* * * * *'
    }


    stages {
      stage('Compile') {
         steps {
           sh 'mvn compile' //only compilation of the code
          }
    }

    stage('SonarQube Analysis') {
            steps {
              withSonarQubeEnv(installationName: 'petclinic'){
                 sh 'mvn clear verify soanr:sonar'
              }
            }  
    }

    // stage('Snyk Test') {
    //   steps {
    //     echo 'Snyk Testing...'
    //     snykSecurity(
    //       snykInstallation: 'petclinic-test',
    //       snykTokenId: 'petclinic-snyk',
    //       // place other parameters here
    //     )
    //   }
    // }

    }
        
}                
        // stage("Quality Gate"){
        //     steps{
        //         script{
        //             TEMP_STAGE_NAME=env.STAGE_NAME
        //             timeout(time: 1, unit: 'HOURS') 
        //             {
        //                 waitForQualityGate abortPipeline: true
        //                 def qg= waitForQualityGate()
        //                 if (qg.status!= 'OK'){
        //                     error "Pipeline aborted due to quality gate failure: ${qg.status}"
        //                 }
        //             }         
        //             echo 'Quality Gate Passed' 
        //         }
        //     }
        // }





//     }
// }

// }


    
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



