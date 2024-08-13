pipeline {
    agent any
    tools{
        nodejs 'node16'
    }
    environment {
        SONAR_SCANNER = tool 'sonar-scanner'  // Ensure this tool name matches the configuration in Jenkins
    }

    stages {
        stage('Clone the Repository') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/saeedhmohd244/zomato.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar-scanner') {  // Use the correct SonarQube environment
                    script {
                        sh '''${SONAR_SCANNER}/bin/sonar-scanner \
                            -Dsonar.projectName=zomato \
                            -Dsonar.projectVersion=1.0 \
                            -Dsonar.projectKey=zomato \
                            -Dsonar.host.url=http://34.238.252.251:9000 \
                            -Dsonar.login=d7a60efbb6e62c553b4796ca244203472bbc9a1f'''
                    }
                }
            }
        }

        stage('dependency check'){
            steps{
                dependencyCheck additionalArguments: '--scan ./ --disableYarnAudit --disableNodeAudit', odcInstallation: 'DC-check'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
    }
    
    
}






