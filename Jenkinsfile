
pipeline {
    //agent any
    agent { label 'onlinebookstore' }

    stages {
        stage('Pull Stage') {
            steps {
               git 'https://github.com/vaishalijadhav2418/onlinebookstore_Source_code.git'
                sh '''ls'''
                sh 'pwd'
                echo 'Pull stage succeed'
            }
        }
        stage('Build Stage') {
            steps {
                sh '/opt/maven/bin/mvn clean package '
                echo 'Build Stage succeed'
            }
        }
        
       stage('Test stage') {
    steps {
        sh '''
            export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
            export PATH=$JAVA_HOME/bin:$PATH
            java -version

        '''

       sh ''' 
            /opt/maven/bin/mvn sonar:sonar \
             mvn clean verify sonar:sonar \
              -Dsonar.projectKey=Onlinebookstore \
              -Dsonar.projectName='Onlinebookstore' \
              -Dsonar.host.url=http://13.235.247.241:9000 \
              -Dsonar.token=sqp_e48c293ab9e4d3346f3f5925632c56fc858be828
            '''

        echo 'Testing done'
    }
}

    
        
        stage('Deploy Stage') {
            steps {
                echo 'Deployment Done '
            }
        }
    }
}
