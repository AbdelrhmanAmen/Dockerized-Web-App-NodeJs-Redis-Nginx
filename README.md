# Dockerized-Web-App-NodeJs-Redis-Nginx
---
Docker Compose is a Python package to:
- Automate the build of an application with all its services
- Define the services that make up your application in a single file

The Application we want to run consist of **4** services (nginx - redis - web1 - web2)
- web1 and web2 are just NodeJs web applications.
- nginx exposed to public access and act as load balancer.
- redis is in-memory cache to store the count of visits.

<p align="center">
  <img src="https://github.com/AbdelrhmanAmen/Dockerized-Web-App-NodeJs-Redis-Nginx/assets/73068684/3abd7a26-9732-486b-9f5c-6e1761e31479" width="700" height="400" alt="image description"/>
</p>

## Steps
- Create a docker-compose.yml
- Define redis service to run the image `redis:alpine` and listen on the port `6379` mapped to `6379` on the host
- Create a Dockerfile to build cutomized Nginx image based on `nginx` official image:
  - Configure Nginx as a load balancer, for that we need to edit the main configuration file in  `/etc/nginx/nginx.conf`
  - Nginx will listen on port `80`
- Create a Dockerfile to build the Web App image based one `node:alpine` official image:
  - Copy the application source code into a working directory
  - Install application's dependencies 
  - Run the application, by default it is configured to use the port `5000`

## Services Dependencies:
  > - Web Apps depends on redis
  > - Nginx depends on Web Apps
 
 That is why it was important to create the docker-compose file that way.
