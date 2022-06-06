pipeline {
    agent any

    environment {
        BACKEND_PROJECT_NAME = "ps-backend"
        FRONTEND_PROJECT_NAME = "ps-frontend"
        DB_USER = "postgres"
        DB_PASS = "postgres"
        DB_HOST = "database"
        DB_DATABASE = "postgres"
        DB_PORT = "5432"
        APP_HOST = "0.0.0.0"
        APP_PORT = "8000"
    }

    stages {
        stage("Prepare") {
            steps {
                deleteDir()
                git branch: "main", url: 'https://github.com/idfortytwo/pscheduler-prod'
            }
        }

        stage("Get artifacts") {
            steps {
                copyArtifacts(projectName: "$BACKEND_PROJECT_NAME")
                sh "unzip sources.zip -d backend/sources"
                copyArtifacts(projectName: "$FRONTEND_PROJECT_NAME")
                sh "unzip static.zip -d frontend/static"
            }
        }

        stage("Build docker image") {
            steps {
                dir('backend/sources/pscheduler') {
                    sh "touch .env"
                    sh "echo DB_USER=$DB_USER >> .env"
                    sh "echo DB_PASS=$DB_PASS >> .env"
                    sh "echo DB_HOST=$DB_HOST >> .env"
                    sh "echo DB_DATABASE=$DB_DATABASE >> .env"
                    sh "echo DB_PORT=$DB_PORT >> .env"
                    sh "echo APP_HOST=$APP_HOST >> .env"
                    sh "echo APP_PORT=$APP_PORT >> .env"
                }

                sh "docker-compose -f docker-compose-jenkins-build.yaml build"
            }
        }
    }
}
