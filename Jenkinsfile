pipeline {
    agent any
    tools {
        maven 'maven3'
        jdk 'java17'
    }
    stages {
        stage('Download the Git Code') {
            steps {
                echo 'Download the Git Code'
                git branch: 'main', url: 'https://github.com/knpatel404/maven-jenkins6.git'
            }
        }
        stage('Build the Code') {
            steps {
                echo 'Build the Code'
                sh 'mvn clean package'
            }
        }
        stage('Deploy the Code') {
            steps {
                echo 'Deploy the Code'
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage('Build a new Job') {
            steps {
                echo 'Build a new Job'
                build wait: false, job: 'java-deploy-script'
            }
        }
    }
}
