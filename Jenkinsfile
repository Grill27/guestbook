peline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url:'https://github.com/Grill27/guestbook.git'
            }
        }
        stage('Build') {
            steps {
                sh './mvnw clean compile'
            }
        }
        stage('Unit Test') {
            steps {
                sh './mvnw test'
            }
            
            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }

        stage('SonarQube Analysis') {
            echo 'SonarQube Analysis'
            // steps{
            //     withSonarQubeEnv('SonarQube-Server'){
            //         sh '''
            //             ./mvnw sonar:sonar \
            //             -Dsonar.projectKey=guestbook \
            //             -Dsonar.host.url=http://192.168.56.143:9000 \
            //             -Dsonar.login=071444a4a1fe9176a224c1d6ff6722c6c2fae596
            //         '''
            //     }
            // }
        }
        stage('SonarQube Quality Gate'){
            echo 'SonarQube Quality Gate'
            // steps{
            //     timeout(time: 2, unit: 'MINUTES') {
            //         script{
            //             def qg = waitForQualityGate()
            //             if(qg.status != 'OK') {
            //                 echo "NOT OK Status: ${qg.status}"
            //                 error "Pipeline aborted due to quality gate failure: ${qg.status}"
            //             } else{
            //                 echo "OK Status: ${qg.status}"
            //             }
            //         }
            //     }
            // }
        }
    }
}


