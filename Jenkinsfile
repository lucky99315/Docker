<<<<<<< HEAD
node {

// call notify function

 notify('Started')    
 
 stage ('SCM_Checkout') {
    checkout([$class: 'GitSCM', 
        branches: [[name: '*/master']], 
        doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], 
        userRemoteConfigs: [[url: 'https://github.com/lucky99315/Maven-petclinic-project.git']]])
 }

 stage ('Build_Test and Package') {
    sh 'mvn clean package'
 //   junit 'target/surefire-reports/TEST*.xml'
 }
 
// stage ('Publish reports') {
//    publishHTML(target: [allowMissing: true, 
 //                alwaysLinkToLastBuild: false, 
  //               keepAll: true, 
  //               reportDir: 'target/site/jacoco', 
  //               reportFiles: 'index.html', 
  //               reportName: 'HTML Report', 
  //               reportTitles: 'Code Coverage-Report'])
 }
 
 stage ('Archive and Notify') {

    archiveArtifacts 'target/*.war' 

//invoke build-in email function

    step([$class: 'Mailer', 
        notifyEveryUnstableBuild: true, 
        recipients: 'cc:<luckykumar99315@gmail.com>', 
        sendToIndividuals: false])
 }
 
 notify ('Waiting for Deployment')
 
 //wait for approval
 
 input 'Deploy to Staging?'
 
 // stage ('Deploy to AppServer') {
 //sh 'cp target/petclinic.war /opt/apache-tomcat-8.5.21/webapps'
 //sh 'sudo /opt/apache-tomcat-8.5.21/bin/shutdown.sh'
 //sh 'sudo /opt/apache-tomcat-8.5.21/bin/startup.sh'
 //}
 
 // push build to git repository
 // sh 'git push https://<username>:<password>@github.com/<path-to-git-repo> --all'
 
 notify('Completed')  
}

 def notify(status) {
  mail (
        body:"""${status}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':
                 Check console output at, 
                 href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]""",
        cc: 'ganeshhp@gmail.com', 
        subject: """JenkinsNotification: ${status}:""", 
        to: 'luckykumar99315@gmail.com'  
       ) 
 }
=======
node {
    
 notify('Started')
 
 stage ('SCM_Checkout') {
    checkout([$class: 'GitSCM',
        branches: [[name: '*/master']],
        doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [],
        userRemoteConfigs: [[url: 'https://github.com/ganeshhp/Maven-petclinic-project.git']]])
 }
 stage ('Build_Test and Package') {
    sh 'mvn clean verify package'
 //   junit 'target/surefire-reports/TEST*.xml'
 }
 
 stage ('Archive and Notify') {
    publishHTML(target: [allowMissing: true,
                 alwaysLinkToLastBuild: false,
                 keepAll: true,
                 reportDir: 'target/site/jacoco',
                 reportFiles: 'index.html',
                 reportName: 'HTML Report',
                 reportTitles: 'Code Coverage-Report'])
    archiveArtifacts 'target/*.war'
    step([$class: 'Mailer',
        notifyEveryUnstableBuild: true,
        recipients: 'cc:ganesh@automationfactory.in',
        sendToIndividuals: false])
 }
 notify ('Waiting for Deployment')
 
 input 'Deploy to Staging?'
 
 stage ('Deploy to AppServer') {
 sh 'cp target/petclinic.war /opt/apache-tomcat-8.5.21/webapps'
 sh 'sudo /opt/apache-tomcat-8.5.21/bin/shutdown.sh'
 sh 'sudo /opt/apache-tomcat-8.5.21/bin/startup.sh'
 }
 
 // sh 'git push https://ganeshhp:<password>@github.com/ganeshhp/Maven-petclinic-project.git --all'
 
 notify('Completed')
}
 def notify(status) {
  mail (
        body:"""${status}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':
                 Check console output at,
                 href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]""",
        cc: 'support@automationfactory.in',
        subject: """JenkinsNotification: ${status}:""",
        to: 'ganesh@automationfactory.in'
       )
 }
>>>>>>> 1538a2ea55dab218fa06434d40471ae7fd0496fa
