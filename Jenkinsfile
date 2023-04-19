node('JDK_17') {
    stage('version control') {
        git url: 'https://github.com/dksinformations/game-of-life.git',
            branch: 'scripted'
    }
    stage('build the code') {
        sh 'export PATH="/usl/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'
    }
    stage('archive the artifacts') {
        archiveArtifacts onlyIfSuccessful: true,
            artifacts: '**/target/gameoflife.war',
            allowEmptyArchive: false
    }
    stage('show the test results') {
        junit testresults: '**/surefire-reports/TEST-*.xml',
         allowEmptyResults: true
    }
}
