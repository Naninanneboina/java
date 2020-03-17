pipeline{
    agent any
    tools{
        jdk 'jdk1.8'
        maven 'maven3'
            }
            options{
                timestamps()
                 properties([[$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '10']]]);

            }
            stages{
                stage('Display PATH OF JENKINS'){
                    steps{
                        sh '''
                        echo "This is declerative pipeline for building serviceapp"
                        echo "PATH = ${PATH}
                        '''
                        }
                }
                stage('chekout the source code'){
                    steps{
                      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'e7d4ad1a-97f5-40ca-927d-246258c87fd6', url: 'https://github.com/Naninanneboina/serviceapp.git']]])
                    }
                }
                stage('Building the source using maven'){
                    steps{
                        sh 'mvn clean compile install'
                    }
                }
            }
}
