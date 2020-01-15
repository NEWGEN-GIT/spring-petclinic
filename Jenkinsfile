pipeline{
    agent any
    tools {
        maven 'maven3'
        jdk 'jdk8'
    }
    stages{
            stage("SCM"){
            steps{
                
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/NEWGEN-GIT/spring-petclinic']]])
            }
        }
        
        stage("Build"){
            steps{
                bat 'mvn clean package'
            }
        }
        

        stage("Code Analysis"){
            steps{
                bat 'mvn sonar:sonar -Dsonar.host.url=http://192.168.56.241:9000'
            }
        }
        

        
  }
}

