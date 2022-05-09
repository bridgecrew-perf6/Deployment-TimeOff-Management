
Deployment TimeOff Management

Architecture Proposed to Release New versions of Timeoff Management Application.

![interview drawio (1)](https://user-images.githubusercontent.com/7906235/167472027-c27bbdfe-afdc-49b4-9888-bcb8744834d6.png)

This is a CI/CD Propose to create and artifact in docker, and every latest version should be deployed in docker as a service. Deployment phase use a rolling update strategy to avoid timeout of the application.

Tools Required:
- Jenkins
  + Plugins: Docker Common Plugin, Docker Pipeline, Docker Plugin.
- Docker Engine
- Github Account.
- Docker Hub Account. 

Workflow:

1. Fork https://github.com/timeoff-management/timeoff-management-application github repository.
2. Create a webhook, in the new repository.
3. Create a pipeline in Jenkins.
  3.1. Set up pipeline to download the script https://github.com/cobbgcall/Deployment-TimeOff-Management.git/CreateArtifact/, this Jenkisfile, create a docker image according to Dockerfile in the timeoff-management-application repository, and pull to docker hub two version of it, one version with the build number as a tag, and other overwriting latest tag version.
4. Set up webhoook in the docker hub repository cobbgcloud/timeoff.
5. Create a second pipeline to create or update docker service. It should have set up https://github.com/cobbgcall/Deployment-TimeOff-Management.git/CreateArtifact/.
