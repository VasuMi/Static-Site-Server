# Static Site Server

## Project Overview

This project demonstrates how to set up a basic Linux web server using Nginx and serve a static website. It also demonstrates how to use `rsync` to deploy and update the website on a remote server.

## Technologies Used

* Linux / Ubuntu
* Nginx
* HTML
* CSS
* Images
* SSH
* rsync
* Bash

## 1. Set Up Remote Linux Server

A remote Ubuntu Linux server was created using a cloud provider.

SSH was used to connect to the server:

```bash
ssh USER@SERVER_IP
```

## 2. Install Nginx

The server was updated and Nginx was installed:

```bash
sudo apt update
sudo apt install nginx -y
```

The Nginx service was checked using:

```bash
sudo systemctl status nginx
```

Nginx serves web content from:

```text
/var/www/html
```

## 3. Create Static Website

A simple static website was created using:

```text
index.html
style.css
images/
```

The website contains basic HTML, CSS styling and image files.

## 4. Deploy Website Using rsync

The local website files were synchronized with the remote server using:

```bash
rsync -avz ./site/ USER@SERVER_IP:/var/www/html/
```

The `rsync` command copies only the required changes, making it useful for updating the website.

## 5. Access the Website

After configuring Nginx, the website can be accessed using the server's IP address:

```text
http://SERVER_IP
```

Nginx receives the HTTP request and serves the static files from `/var/www/html`.

## 6. Deployment Script

A `deploy.sh` script can be used to automate deployment:

```bash
#!/bin/bash

SERVER_USER="USER"
SERVER_IP="SERVER_IP"
REMOTE_PATH="/var/www/html"

rsync -avz ./site/ "$SERVER_USER@$SERVER_IP:$REMOTE_PATH"
```

The script can be executed with:

```bash
chmod +x deploy.sh
./deploy.sh
```

## 7. Project Structure

```text
Static-Site-Server/
│
├── site/
│   ├── index.html
│   ├── style.css
│   └── images/
│
├── deploy.sh
└── README.md
```

## 8. Learning Outcomes

* Set up a basic Linux web server
* Installed and configured Nginx
* Served a static website
* Used SSH to manage a remote server
* Used `rsync` for website deployment
* Created a basic deployment script
* Learned the basics of web server administration

## Security

Private SSH keys, passwords and other sensitive credentials were not included in the repository.


Project Url: https://roadmap.sh/projects/static-site-server
