pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Building the war"
            }
        }

        stage('Deploy to QA') {
            steps {
                echo "Deploying to QA"
            }
        }

        stage('CheckOut') {
            steps {
                git url: 'https://github.com/pravallikanakkagit/Jan2025APIPostCollections'
            }
        }



        stage('Pull Docker Image') {
                    steps {
                        bat 'docker pull pravallikanakka/goresttest:1.0'
                    }
        }

        
        stage('Run API Test Cases') {
                    steps {
                        bat 'docker run -v %cd%/newman:/app/results pravallikanakka/goresttest:1.0'
                    }
        }

        stage('Publish HTML Extra Reports') {
                    steps {
                        publishHTML([
                            allowMissing: false,
                            alwaysLinkToLastBuild: false,
                            keepAll: true,
                            reportDir: 'newman',
                            reportFiles: 'gorest.html',
                            reportName: 'HTML Extra API Report',
                            reportTitles: ''
                        ])
                    }
                }
                
               

        stage('Deploy to PROD') {
            steps {
                echo "Deploying to PROD"
            }
        }
    }
}