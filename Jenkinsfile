<<<<<<< HEAD
pipeline{
    agent none{    
    stages {
        stage('build') {
            steps {
                steps {
                    echo 'build done1'
                    sh './gradlew clean build'
                    }
            }
        }
        stage('upload') {
            steps {
                echo 'updload done.'
                sh 'aws s3 cp build/libs/application.war s3://springboot-cicd-jeon/application.war --region us-east-1'
                }
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
        
    
=======
pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'build done'
      }
    }

    stage('upload') {
      steps {
        echo 'upload done'
      }
    }

    stage('deploy') {
      steps {
        echo 'deploy done'
      }
    }

  }
}
>>>>>>> 35e6b55e296e04b978841705367b5fc4c67caa94
