pipeline {
    agent any
    tools{
        jdk "jdk11"
        maven "maven3"
    }

   stages {
        stage('git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/rajdeepsingh642/Ecart-app.git'
            }
        }
        stage('compile') {
            steps {
             sh "mvn compile"
             }
        }    
       
        stage('build') {
            steps {
             sh "mvn package -DskipTests"
            }
        }

        stage('dockerimage') {
            steps {
             sh "docker build -t ekart:$BUILD_ID ."
          
            }
        }    
         stage('containerrun') {
            steps {
             sh "docker run -p 8070:8070  ekart:$BUILD_ID"
            }
            }
    }



   
}
