node {
   stage ('Preparation'){
       git credentialsId: '469c81a2-ea76-4eb6-9b81-4b8d9604edfd', url: 'git@github.com:scarecrow80/gildedrose.git'
   }
   stage ('Build'){
       sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn clean package'
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'      
   }   
   stage ('Javadoc'){
       sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'
       archive 'target/gildedrose-*.jar'
       archive 'target/javadoc'
   }
}
