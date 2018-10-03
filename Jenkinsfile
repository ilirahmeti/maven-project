pipeline {
    agent any
    stages{ 
 
        stage ("mvn clean") {
    withEnv( ["PATH+MAVEN=${tool name: 'mvn', type: 'maven'}/bin"] ) {
      sh "mvn clean install -Dmaven.test.skip=true -Dfindbugs.skip=true"
    }
}
        
        stage('Build'){
            steps {
                sh 'mvn clean test'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}

