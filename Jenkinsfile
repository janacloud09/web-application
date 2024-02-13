pipeline {
    agent any

    triggers {
         cron 'H/1 * * * *'
          }

    tools {
  maven 'Maven381'
}
 options {
  buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '2', numToKeepStr: '3')
}

    stages {
        stage('Clone the Repo from GitHub') {
            steps {
                git credentialsId: 'github_user_password', url: 'https://github.com/janacloud09/web-application.git'
            }
        }      
    stage('Build the Code using Maven') {
            steps {
                sh ' mvn clean install '
            }
        }        
    stage('Deploy war file to Tomcat7') {
            steps {
deploy adapters: [tomcat7(credentialsId: 'tomat_user_password', path:'',url: 'http://65.0.176.170:8080')], contextPath: null, war: '**/*.war'
            }
        }    
    }
}
