# Task-8---Web-Server-Hardening

## Setting up Self-Signed SSL Certs for Nextcloud

First clone this repo and create a certs directory within the repo (I couldn't put an empty directory with git)

cd into the certs directory

Next use this command to set up the private key and the public certificate

```sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /home/student/nextcloud/certs/key.pem -out /home/student/nextcloud/certs/cert.pem```

Make sure that you have your ssl certs, then go to the nextcloud directory to make your custom docker image of nextcloud with ssl

## Setting up the docker container
Make sure that the setssl.sh has executable permissions

```chmod +x setssl.sh```

Then create the docker image with this command

```sudo docker build --tag nextcloud_ssl .```

And finally run the docker container like this

```sudo docker run -d -p 8443:443 -v nextcloud:/var/www/html -v /home/student/nextcloud/certs/:/etc/ssl/nextcloud nextcloud_ssl```

