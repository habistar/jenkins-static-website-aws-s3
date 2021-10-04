pipeline {
    agent any

    stages{
        stage('deploy to S3'){
            steps{
                sh 'aws s3 cp public/index.html s3://habiba-static'
                sh 'aws s3api put-object-acl --bucket habiba-static --key index.html --acl public-read'
                sh 'aws s3 cp public/error.html s3://habiba-static'
                sh 'aws s3api put-object-acl --bucket habiba-static --key error.html --acl public-read'
            }
        }
    }
    post{
        always{
            cleanWs disableDeferredWipeout: true, deleteDirs: true
        }
    }

}