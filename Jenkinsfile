pipeline {
    agent any
    stages{ 
        stage('Git') {
            steps {
                step([$class: 'WsCleanup'])
                checkout scm
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
}
