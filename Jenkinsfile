pipeline {

    agent any

     
    stages {
        
        stage ('checkout'){
            steps {
            git  'https://github.com/dinrag/srinu.git'
            }
        }

        stage ('compile') {

            steps {

                withMaven(maven : '/opt/mvn/apache-maven-3.6.3') {

                    sh 'mvn clean compile'

                }

            }

        }

    



        stage ('test') {

            steps {

                withMaven(maven : '/opt/mvn/apache-maven-3.6.3') {

                    sh 'mvn test'

                }

            }

        }

        

        

        stage ('package') {

            steps {

                withMaven(maven : '/opt/mvn/apache-maven-3.6.3') {

                    sh 'mvn package'
                   

                }

            }

         }
         
        stage('deploy') {
            steps{
            sshagent(['tomcat-new1']) {
                sh """  
                     ssh -o StrictHostKeyChecking=no target/TomcatMavenApp-2.0.war  root@10.128.0.2/home/dineshreddy99077/noida/apache-tomcat-7.0.103/webapps/
                     ssh root@10.128.0.2 /home/dineshreddy99077/noida/apache-tomcat-7.0.103/bin/shutdown.sh
                     ssh root@10.128.0.2 /home/dineshreddy99077/noida/apache-tomcat-7.0.103/bin/startup.sh

                """
            }
            }
        }

    }

}
