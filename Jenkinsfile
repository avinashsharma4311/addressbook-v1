pipeline {
    agent none

    tools {
        maven 'mymaven'
    }

    stages {
        stage('Compiling') {
            agent any
            steps {
                echo 'Compiling the Code'
                sh 'mvn compile'
            }
        }
        stage('Code Review') {
            agent any
            steps {
                echo 'Code Review the Code'
                sh 'mvn pmd:pmd'
            }
        }
        stage('Unit Test') {
            agent any
            steps {
                echo 'Unit Testing of the Code'
                sh 'mvn test'
            }
        }
        stage('Coverage Analysis') {
            agent any
            steps {
                echo 'Coverage Analysis the Code'
                sh 'mvn verify'
            }
        }
        stage('Packaging') {
            agent { label 'Jenkins-Slave' }
            steps {
                echo 'Packaging the Code'
                sh 'mvn package'
            }
        }
        stage('Publishing Artifect') {
            agent any
            steps {
                echo 'Publishing artifect to Jfrog'
                sh 'mvn -U deploy -s settings.xml'
            }
        }
    }
}
