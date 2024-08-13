pipeline {
    agent any
	 
    environment {
        SONAR_SCANNER = tool 'sonar-scanner'
    }
    stages {
        stage('Clone the Repository') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/saeedhmohd244/zomato.git'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    sh '''${SONAR_SCANNER}/bin/sonar-scanner \
                        -Dsonar.projectName=zomato \
                        -Dsonar.projectVersion=1.0 \
                        -Dsonar.projectKey=zomato \
                        -Dsonar.host.url=http://52.207.214.177:9000/ \
                        -Dsonar.login=d7a60efbb6e62c553b4796ca244203472bbc9a1f'''
                }
            }
        }
    }
}

