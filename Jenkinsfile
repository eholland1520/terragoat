 
 pipeline {
     environment {
      BEARER_TOKEN = credentials("bearer_token")
      TWISTLOCK_URL = credentials("prisma_serverless_url")
    }
   
    agent any 
    stages {
        stage('Download Twistlock Dependency') { 
            steps {
                 sh '''#!/bin/bash
                  echo "Download Twistlock Defender Binary";
                  rm twistlock_serverless_defender.zip;
                  curl -sSL -k --header "authorization: Bearer $BEARER_TOKEN" -X POST $TWISTLOCK_URL/api/v1/defenders/serverless/bundle -o twistlock_serverless_defender.zip -d "{\"runtime\":\"dotnetcore3.1\",\"provider\":\"azure\"}";
                  ls;
                  pwd;
                  unzip ./twistlock_serverless_defender.zip;
                '''
            }
        }
    }
 }
