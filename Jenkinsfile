pipeline { 
    agent any stages { 
        stage('build') { 
            steps { sh './gradlew clean build' } 
        } 
        stage('upload') { 
            steps { 
                sh 'aws s3 cp build/libs/application.war s3://springboot-cicd-jeon/application.war --region us-east-1'
            }
        } 
        stage('deploy') { 
            steps {
                echo 'deploy done.'
                sh 'aws elasticbeanstalk create-application-version --region us-east-1 --application-name springboot-cicd-jeon --version-label ${BUILD_TAG} --source-bundle S3Bucket="springboot-cicd-jeon",S3Key="application.war"' 
                sh 'aws elasticbeanstalk update-environment --region us-east-1 --environment-name Springbootcicdjeon-env --version-label ${BUILD_TAG}'   
                }
        } 
    } 
}