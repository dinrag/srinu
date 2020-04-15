pipeline {

    agent any

     
    stages {

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
         
        

        

    }

}

