# Process Scheduler
Docker application for scheduling scripts with WebUI.

Allows you to:
- Create cron, interval and date triggered tasks
- Manage tasks execution
- Monitor process output real-time 
- Log all task execution and output


## Usage
### Deploy
Download and run `docker compose up` with `docker-compose.yaml` configuration

### Build using Jenkins
To modify the application:
1. Create three Jenkins pipelines from SCM:
   - prod
   - [backend](https://github.com/idfortytwo/pscheduler-backend)
   - [frontend](https://github.com/idfortytwo/pscheduler-frontend)
2. Modify code in backend or frontend repositories
3. Run backend and frontend pipelines to build the artifacts
4. Set Jenkins pipeline names `BACKEND_PROJECT_NAME` and `FRONTEND_PROJECT_NAME` in `Jenkinsfile`
5. Modify environment variables in prod pipeline and docker configuration in `docker-compose-jenkins-build.yaml`
6. Run prod pipeline to build docker images


## Other repositories
- [Backend repository](https://github.com/idfortytwo/pscheduler-backend)
- [Frontend repository](https://github.com/idfortytwo/pscheduler-frontend)
