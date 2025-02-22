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


## 🏗 Project Architecture
<img src=""/>

## ⚙️ Project Configuration:
### Creating Docker Hosted Repository on Nexus
1. Access Nexus repository, then create a Docker-hosted repository.
2. Create role with the necesarry privileges and assign it to the Docker repository.

### Configuring Nexus to manage and store Docker Images
1. Create a connector in Nexus wthat enables docker clients to connect direclty to the docker-hosted repository.
2. Configure the Droplet firewall to allow traffic on port 8083 for Nexus.
3. Configure and enable the Docker Token in the Realms section.
4. Enable access to insecure registries in docker daemoen by modifying the daemon.json file, which is located **/etc/docker/daemon.json**. If the file does not exist, then create a new one.
5. Restart docker daemon to apply the changes.

### Building & Pushing Image to Nexus
1. Login to Nexus.
2. Build the image.
3. Tag the image.
4. Push image to Nexus.
5. Verify that the image is available in the repository.
