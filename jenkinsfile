pipeline {
    agent {
        node {
            label 'jenkins-agent'
        }
    }
    stages {
        stage('Continuous Integration') {
            steps {
                git branch: 'main', url: 'https://github.com/fredericEducentre/jenkins_project_go.git'
                sh '''
                 sonar-scanner \
                    -Dsonar.projectKey=jenkins_project_go \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://192.168.0.133:9000 \
                    -Dsonar.token=sqp_2b04e6d69eed954c7a38852292b336c2c2011b3a
                '''
            }
        }
        stage('Continuous delivery') {
            steps {
                sh 'docker build . -t jenkins_project_go'
            }
        }
    }
}