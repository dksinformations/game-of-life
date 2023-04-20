pipeline {
    agent { label 'JDK_17' }
    stages {
        stage('VCS') {
            steps {
                git url: 'https://github.com/dksinformations/game-of-life.git'
                    branch: 'declarative'
            }
        }
        stage('package') {
            steps {
                environment {
                    PATH= '/usr/lib/jvm/java-1.8.0-openjdk-amd64'
                }
                sh 'mvn package'
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war'
                                 onlyIfSuccessful: true
                junit testresults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}
