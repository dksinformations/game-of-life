pipeline {
    agent { label 'JDK_17' }
    stages {
        stage('vcs') {
            steps {
                git branch: 'declarative', url: 'https://github.com/dksinformations/game-of-life.git'
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
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}
