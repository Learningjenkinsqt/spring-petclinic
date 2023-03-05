pipeline {
    agent { label 'MAVEN_8' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/Learningjenkinsqt/spring-petclinic.git',
                    branch: 'declarative'
            }
        }
        stage('package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/*.txt',
                   onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}