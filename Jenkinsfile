pipeline {
    agent any

    tools {
        maven 'mymaven'
    }

    stages {
        stage('Compiling') {
            steps {
                echo 'Compiling the Code'
                sh 'mvn compile'
            }
        }
        stage('Code Review') {
            steps {
                echo 'Code Review the Code'
                sh 'mvn pmd:pmd'
            }
        }
        stage('Unit Test') {
            steps {
                echo 'Unit Testing of the Code'
                sh 'mvn test'
            }
        }
        stage('Coverage Analysis') {
            steps {
                echo 'Coverage Analysis the Code'
                sh 'mvn verify'
            }
        }
        stage('Packaging') {
            steps {
                echo 'Packaging the Code'
                sh 'mvn package'
            }
        }
        stage('Publishing Artifect') {
            steps {
                echo 'Publishing artifect to Jfrog'
                sh 'mvn -U deploy -s settings.xml'
            }
        }
    }
}
