pipeline {
    
    agent any

    stages {
        
        stage('Init') {
            steps {
                git 'https://github.com/Victoremepunto/angular-dummy.git'
            }
        }
        
        stage('Example Build and Test') {
            agent { 
                docker {
                    image 'circleci/node:10.15.3-browsers'
                    reuseNode true
                }
            }
            steps {
                sh 'npm i'
                sh 'npm run test-headless'
                publishCoverage adapters: [istanbulCoberturaAdapter('coverage/angular-unit-testing/cobertura-coverage.xml')], sourceFileResolver: sourceFiles('NEVER_STORE')
            }
        }
    }
}
