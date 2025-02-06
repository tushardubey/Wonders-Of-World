pipeline {
    agent any

    stages {
        //Cloning clode
        stage('Clone Code') {
            steps {
                git url: "https://github.com/tushardubey/Wonders-Of-World.git", branch: "main"
            }
        }
        //Sec_Repoort
        stage('SonarQube QA'){
            environment {
                scannerHome = tool 'sonar'
            }
            steps {
                script {
                    withSonarQubeEnv('Sonar'){
                        sh "$Sonar_Home/bin/sonar-scanner \
                        -Dsonar.projectKey=Wonders-of-world \
                        -Dsonar.projectName=Wonders-of-world"
                    }
                }
            }
        }
        stage("quality gate"){
            timeout(time: 1, unit: 'MINUTES'){
                waitForQualityGate abortPipeline: false
            }
        }

        stage('Owasp_Dependency_Check'){
            steps{
                dependencyCheck additionalArguments: '--scan ./', odcInstallation: 'owasp'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }

        stage('file_System_Scan'){
            steps {
                sh ("trivy fs --format table -o trivy-repost.html .")
            }
        }
        
        //Deployment
        stage('deployment using docker'){
            steps {
                sh "docker-compose up -d"
            }
        }

    }
}
