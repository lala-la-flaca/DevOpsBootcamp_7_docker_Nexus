# 🐳 Creating a Docker Repository on Nexus & Pushing an Image

## Description
This demo project is part of Module 7: Containers with Docker from the Nana DevOps Bootcamp. It focuses on setting up a Docker repository on Nexus, configuring it for image storage, and pushing a Docker image to the repository.

<br />

## 🚀 Technologies Used

- <b>Docker for containerization.</b>
- <b>Linux: Ubuntu for Server configuration and management.</b>
- <b>NodeJs/npm: Nana's application from DevOps Bootcamp and package manager.</b>
- <b>Nexus: Private docker repository hosted on DigitalOcean.</b>

## Prerequisites
- <b>Ensure that Nexus Repository from module 6 is up and running.</b>

## 🎯 Features

- <b>Create a docker hosted repository on Nexus</b>
- <b>Configure Nexus to manage and store Docker images.</b>
- <b>Build and Push Docker Image.</b>
- <b>Fetching Image with Nexus API.</b>


## 🏗 Project Architecture
<img src="" width=800 />

## ⚙️ Project Configuration:
### Creating Docker Hosted Repository on Nexus
1. Access the Nexus repository, then create a Docker-hosted repository.
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/Create%20a%20docker%20Hosted%20Repo%20in%20NExus.png" width=800 />
2. Create a role with the necessary privileges and assign it to the Docker repository.
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/2%20Adding%20docker-hosted%20privileges.png" width=800 />

### Configuring Nexus to manage and store Docker Images
1. Create a connector in Nexus that enables docker clients to connect directly to the docker-hosted repository.
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/Adding%20the%20port%20to%20docker%20repo%20nexus.png" width=800 />
2. Configure the Droplet firewall to allow traffic on port 8083 for Nexus.
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/Enabling%20Port%20In%20Droplets%20firewall.png" width=800 />
3. Configure and enable the Docker Token in the Realms section.
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/ActivatingDcokerTokenNexus.png" width=800 />
4. Enable access to insecure registries in the docker daemon by modifying the daemon.json file, which is located **/etc/docker/daemon.json**. If the file does not exist, then create a new one.
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/creating%20DockerDaemonJson%20file.PNG" width=800 />
5. Restart the docker daemon to apply the changes.
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/restating%20docker%20daemon.PNG" width=800 />

### Building & Pushing Images to Nexus
1. Login to Nexus.

   ```bash
   docker login HTTP://157.230.56.153:8083
   ```   
  
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/Login%20to%20DockerNexusRepo.PNG" width=800 />
   
2. Navigate to the app folder in the application and build the image.

   ```bash
   docker build -t js-app:1.0 .
   ```
   
4. Tag the image.

   ```bash
   docker tag js-app:1.0 157.230.53.153:8083/js-app:1.0
   docker images
   ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/TagImage.png" width=800 />
   
5. Push the image to Nexus.

   ```bash
   docker push 157.230.53.153:8083/js-app:1.0
   ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/PushingImageToDockerNExus.PNG" width=800 />
   
6. Verify that the image is available in the repository.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_Nexus/blob/main/Img/DockerImageAvailableNexus.png" width=800 />


### Fetching Docker Image
1. Fetching image with Nexus API
   
   ```bash
   curl -u docker:docker -X GET 'http://157.230.56.153:8081/service/rest/v1/components?repository=docker-hosted'
   ```
