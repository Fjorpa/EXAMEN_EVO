pipeline {
    agent any
    tools { 
        maven 'MAVEN_3_6_3' 
        jdk 'JDK_1_11' 
    }
	
    stages {
        stage ('Compile Stage 07/07/2022') {

            steps {
                withMaven(maven : 'MAVEN_3_6_3') {
                    bat 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'MAVEN_3_6_3') {
                    bat 'mvn test'
                }
            }
        }

        stage ('Package Stage') {
            steps {
                withMaven(maven : 'MAVEN_3_6_3') {
                    bat 'mvn package'
                }
            }
        }

		stage('Deployment stage') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL} direction ${env.WORKSPACE}"
                withMaven(maven : 'MAVEN_3_6_3') {
					bat '"C:\\Program Files\\Git\\mingw64\\bin\\curl.exe" -T ".\\target\\sistema-ventas-spring.war" "http://deployer:orive@localhost:8080/manager/text/deploy?path=/sistema-ventas-spring&update=true"'
                } 
            }
        }

    }
}
