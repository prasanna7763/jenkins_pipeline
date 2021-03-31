node{

    checkout scm
    def mvnHome
    dir('BuildQuality'){
        stage('Preparation'){
                        
           // git 'https://github.com/prasanna7763/simple-spring.git'
          //  mvnHome = tool 'Maven'
        }

        stage('Build') {
            // Run the maven build
         /*   if (isUnix()) {
                sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
            } else {
                bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
            } */
        }
        
        stage('SonarQube Analysis') { 
           // def mvnHome
            //mvnHome = tool 'Maven'
// //           withSonarQubeEnv('Sonar') { 
//                 if (isUnix()) {
//                     sh "'${mvnHome}/bin/mvn' org.sonarsource.scanner.maven:sonar-maven-plugin:3.3.0.603:sonar -f pom.xml "+ 
//                     " -Dsonar.projectKey=org.sonarqube:java-sonar " +
//                     " -Dsonar.projectKey=org.sonarqube:java-sonar " +
//                     " -Dsonar.projectName='Java :: Simple Spring Project' " +
//                     " -Dsonar.projectVersion=1.0 " +
//                     " -Dsonar.language=java " +
//                     " -Dsonar.sources=. " +
//                     " -Dsonar.tests=. " +
//                     " -Dsonar.test.inclusions='**/*Test*/**' " +
//                     " -Dsonar.exclusions='**/*Test*/**' "
//                 } else {
//                     bat (/"${mvnHome}\bin\mvn" org.sonarsource.scanner.maven:sonar-maven-plugin:3.3.0.603:sonar -f pom.xml -Dsonar.projectKey=org.sonarqube:java-sonar -Dsonar.projectName="Java :: Simple Spring Project" /)
//                 }    
//             } 
        }

        stage('Unit Test Results') {
//            junit '**/target/surefire-reports/TEST-*.xml'
            //archive 'target/*.jar'
        }

    }
}

stage name:'Deploy to staging', concurrency:1
    node {
                //sh 'sudo docker run -d -p=3000:80 --network=bundlev2_prodnetwork nginx'
//        dir('BuildQuality'){
//        sh 'sudo docker-compose up -d --build'
  //  }
                
}

node('UbuntuSlave') {
    def mvnHome
    dir('FunctionalTests'){

        stage('Get Functional Test Scripts'){                        
              git 'https://github.com/prasanna7763/jenkins-selenium-int-testing.git'
              mvnHome = tool 'MVN'
        }

        stage('Run Tests') {
       //     sh "'${mvnHome}/bin/mvn' -Dgrid.server.url=http://seleniumhub:4444/wd/hub clean test "
        }
        stage('Functional Test Results') {
         //   junit '**/target/surefire-reports/TEST-*.xml'
        }
    }

}

stage name:'Shutdown staging'
    node {
                
        dir('BuildQuality'){
//       sh 'sudo docker-compose stop'
    }
                
}
        

