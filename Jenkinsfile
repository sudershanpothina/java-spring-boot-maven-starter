pipeline {
    agent {
            label "master"
        }

    tools {
        maven "MAVEN_DEFAULT"
    }

    stages {

        stage('checkout') {
            steps {
                git branch: 'jar', url: 'git@github.com:sudershanpothina/java-spring-boot-maven-starter.git'
                stash name:"project", includes: "*"
            }
        }
        stage('Build') { 
            agent {
                label "worker1"
            }
            steps { 
                unstash "project"
                sh "mvn clean "
            }
        }
        stage('Test'){
            agent {
                label "worker2"
            }
            steps {
                unstash "project"
                sh "mvn test"
            }
        }
    }
}
