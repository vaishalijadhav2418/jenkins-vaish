pipeline {
    agent { label 'node' }

    stages {
        stage('Pull Stage') {
            steps {
                git 'https://github.com/vaishalijadhav2418/onlinebookstore_Source_code.git'
                sh 'ls -l'
                sh 'pwd'
                echo 'Pull stage succeed'
            }
        }

        stage('Build Stage') {
            steps {
                sh '''#!/bin/bash
                    cd onlinebookstore_Source_code
                    /opt/maven/bin/mvn clean package
                '''
                echo 'Build Stage succeed'
            }
        }

        stage('Test Stage') {
            steps {
                sh '''#!/bin/bash
                    cd onlinebookstore_Source_code
                    /opt/maven/bin/mvn clean verify sonar:sonar \
                        -Dsonar.projectKey=Obs \
                        -Dsonar.projectName=Obs \
                        -Dsonar.host.url=http://13.233.93.72:9000 \
                        -Dsonar.token=sqp_fd8a441f7a86e8c4393af15ca0ff3652c23833f9
                '''
                echo 'Testing done'
            }
        }

        stage('Deploy Stage') {
            steps {
                echo 'Deployment Done'
            }
        }
    }
}
