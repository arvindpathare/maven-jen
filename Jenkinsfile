pipeline {
   agent any
stages {
        stage('checkout') {
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/master']],
			   doGenerateSubmoduleConfigurations: false,
			   extensions: [], submoduleCfg: [],
			   userRemoteConfigs: [[credentialsId: '3f468ed0-fea8-4ab3-80ac-bff73343900a',
			   url: 'https://github.com/jenkins-docs/simple-java-maven-app.git']]])
            }
        }
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
                echo 'deploy it later'
            }
        }
    }
}
