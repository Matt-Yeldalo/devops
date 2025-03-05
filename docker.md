# Docker Notes

Docker is a containerization platform that allows you to package your application with all its dependencies, 
making it easy to deploy across different environments. Instead of dealing with installation issues and conflicting dependencies, 
you define everything in three files: Dockerfile, docker-compose.yml, and .dockerignore
- Dockerfile
-   The main file that defines how to build the image
- docker-compose.yml
-   For defining services: DB, app info
- .dockerignore
-   Excluding files

## Troubleshooting

1. Open config file sudo nano /etc/resolv.conf and add the following under existing nameservers
    nameserver 8.8.8.8 
    nameserver 8.8.4.4

2. run following commands to restart daemon and docker service
        `sudo systemctl daemon-reload && systemctl restart docker`
