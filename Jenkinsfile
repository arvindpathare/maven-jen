pipeline {
   agent any
   tools {
    maven 'Maven'
  }
stages {
        stage('checkout') {
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/master']],
               doGenerateSubmoduleConfigurations: false, extensions: [],
               submoduleCfg: [],
               userRemoteConfigs: [[credentialsId: '3f468ed0-fea8-4ab3-80ac-bff73343900a',
               url: 'https://github.com/arvindpathare/maven-jen.git']]])
            }
        }
		stage('Build') {
            steps {
                sh 'which mvn'
                sh 'source /etc/profile.d/maven.sh'
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
                sh 'docker build -t arvindpathare/new_project/dev .'
				sh 'docker push arvindpathare/new_project/dev:latest'
            }
        }
    }
}
