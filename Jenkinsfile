pipeline{
    agent any
    tools { 
        maven 'Apache Maven 3.6.3'
    }
    stages {
        stage('Build Maven') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'gittoken', url: 'https://github.com/Gautham-kukutla/jenkins-docker-example.git']]])
                sh "mvn -Dmaven.test.failure.ignore=true clean package"

            }
        }
        stage('Archive Artifacts') {
          steps {  
                   archiveArtifacts artifacts: '**/*.jAr',
                   allowEmptyArchive: true,
                   fingerprint: true,
                   onlyIfSuccessful: true,
                   caseSensitive: false,
                   followSymlinks: false,
                   excludes: "myfol/*"
                  }
              }
         }
  }
