# POC.Jenkins.DoubleVersion

**This project is a proof of concept to make jenkins build 2 .net core projects, each on different versions, 2.2 and 3.1**


1- Build docker image from jenkins, installing .net core 2.2 and 3.1 on OS

`docker build -f .\jenkins.Dockerfile . -t jenkins-local`

2- Run Docker image

`docker container run -d -p 8082:8080 -v jenkinsvol2:/var/jenkins_home --name jenkins-locals jenkins-local`

3- Access UI and configure


get password with this command: 
`docker container exec CONTAINER_ID sh -c "cat /var/jenkins_home/secrets/initialAdminPassword"`

access UI on localhost:8082 and configure with this password.

4- Create pipeline and build;


