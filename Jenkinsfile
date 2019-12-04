pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
		        sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh 'JENKINS_NODE_COOKIE=dontKillMe ../deploy_jar.sh'
            }
        }
    }
}