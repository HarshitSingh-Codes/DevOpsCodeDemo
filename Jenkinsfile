pipeline {
    agent any
    tools {
        maven 'mvn'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/samirkesare/DevOpsCodeDemo.git'
            }
        }
        stage('Build Artifact') {
            steps {
                sh 'mvn clean install'
                echo "Build Artifact done"
            }
        }
        stage('Publish Artifact') {
            steps {
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
                echo "Publishing Artifact done"
            }
        }
        stage('Deploy war file'){
            steps{
            deploy adapters: [tomcat9(credentialsId: 'first_project', path: '', url: 'http://13.114.143.171:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
            }
        }
    }
}
