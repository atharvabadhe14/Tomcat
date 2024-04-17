pipeline {
         agent any
     tool{
maven'local_maven'
     }
         stages {
                 stage('Build') {
                 steps {
                     sh'mvn clean package'
                 }
            post{
success{
echo"Achiving the Artifacts"
achiveArtifacts artifacts: '*/target/.war'
                 }
}
}
                 stage('deploy to tomcat server') {
                 steps{
deploy adapters: [jboss7(credentialsId: 'tomcat', url: 'http://localhost:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
}
}
}
}
