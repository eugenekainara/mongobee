pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
        gitLabConnection('myGitlab')
    }
    tools {
        maven 'Maven-3.5.0'
        jdk 'OpenJDK Runtime Environment 1.8'
    }
    stages {
        stage('build') {
            steps {
                sh 'printenv'
                sh 'mvn clean package'
            }
        }
        stage('test') {
            steps {
                sh 'printenv'
                sh 'mvn test'
            }
        }
        stage('install') {
            steps {
                sh 'printenv'
                sh 'mvn install -DskipTests=true'
            }
        }
    }
    post {
        success {
            archiveArtifacts '**/*.jar, **/*.pom'
        }
    }
}
