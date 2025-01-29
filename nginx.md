# Setting Up an NGINX Web Server: My Journey Through DevOps Stage 0

## Introduction
As an aspiring DevOps engineer, setting up an NGINX web server on a fresh Ubuntu instance felt like the perfect way to dive into web server configuration. This task challenged me to install, configure, and deploy a basic web page using NGINX, marking my first step into infrastructure automation and web hosting.

In this blog, I will walk you through my approach, the challenges I faced, how I resolved them, and what I learned.

## Task Overview
The goal was to:

- Install and configure NGINX on an Ubuntu server.
- Serve a custom HTML page at `/var/www/html/index.html` with the message:
  
  **"Welcome to DevOps Stage 0 - Makanju Favour/Fave"**
  
- Ensure the webpage is accessible via the public IP of the server.
- Document the experience in a blog post.

## Approach to Completing the Task

### Step 1: Provisioning a Cloud Server
I chose to use an AWS EC2 instance (`t2.micro`, Ubuntu 24.04) for this task. I launched the instance with the following setup:

- **OS:** Ubuntu 24.04 LTS  
- **Security Group:** Allowed HTTP (port 80) and SSH (port 22)  
- **Key Pair:** Used for SSH access  

### Step 2: Installing NGINX
After SSH-ing into the server, I updated the package lists and installed NGINX:

```bash
sudo apt update && sudo apt install -y nginx
```

After installation, I confirmed that NGINX was running with:

```bash
sudo systemctl status nginx
```

The output confirmed that NGINX was **active (running).**

### Step 3: Creating the Custom HTML Page
When I navigated to `/var/www/html/`, I noticed that the existing file was named `index.nginx-debian.html` instead of `index.html`.

#### Solution:
I renamed the file using:

```bash
sudo mv /var/www/html/index.nginx-debian.html /var/www/html/index.html
```

Then, I opened it with `vim` to edit the content:

```bash
sudo vim /var/www/html/index.html
```

I added the required content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DevOps Stage 0</title>
</head>
<body>
    <h1>Welcome to DevOps Stage 0 - Makanju Favour/Fave</h1>
</body>
</html>
```

Then, I saved and exited the file (`ESC`, then `:wq`).

### Step 4: Adjusting File Permissions
I ensured that NGINX could read the file:

```bash
sudo chmod 644 /var/www/html/index.html
```

### Step 5: Restarting NGINX
After making changes, I restarted NGINX to apply the updates:

```bash
sudo systemctl restart nginx
```

To verify that the configuration was working, I tested it with:

```bash
sudo nginx -t
```

The output confirmed that the configuration file was correct.

### Step 6: Accessing the Web Page
Then, I entered `http://<my-server-ip>/` in my browser.
my-server-ip = 3.95.230.183

🎉 **It worked!** I saw the message:  
**"Welcome to DevOps Stage 0 - Makanju Favour/Fave"**

## Challenges Faced and How I Solved Them

### 1. `index.html` Not Found Error
When I navigated to `/var/www/html/`, the file `index.html` wasn't missing but had a different name (`index.nginx-debian.html`).

#### Solution:
I renamed it using:

```bash
sudo mv /var/www/html/index.nginx-debian.html /var/www/html/index.html
```

Then, I edited the file using:

```bash
sudo vim /var/www/html/index.html
```

## How This Task Contributes to My Learning and Goals
This task helped me strengthen my foundational skills in:

- Web server configuration using NGINX.
- Linux server management with Ubuntu.
- Cloud deployment on AWS EC2.
- Troubleshooting skills in DevOps.

## References
Throughout this process, I explored roles in DevOps and cloud engineering. If you're interested in learning more, check out:

- [DevOps Engineers](https://hng.tech/hire/devops-engineers)
- [Cloud Engineers](https://hng.tech/hire/cloud-engineers)
- [Site Reliability Engineers](https://hng.tech/hire/site-reliability-engineers)
- [Platform Engineers](https://hng.tech/hire/platform-engineers)
- [Infrastructure Engineers](https://hng.tech/hire/infrastructure-engineers)
- [Kubernetes Specialists](https://hng.tech/hire/kubernetes-specialists)
- [AWS Solutions Architects](https://hng.tech/hire/aws-solutions-architects)
- [Azure DevOps Engineers](https://hng.tech/hire/azure-devops-engineers)
- [Google Cloud Engineers](https://hng.tech/hire/google-cloud-engineers)
- [CI/CD Pipeline Engineers](https://hng.tech/hire/ci-cd-pipeline-engineers)
- [Monitoring/Observability Engineers](https://hng.tech/hire/monitoring-observability-engineers)
- [Automation Engineers](https://hng.tech/hire/automation-engineers)
- [Docker Specialists](https://hng.tech/hire/docker-specialists)
- [Linux Developers](https://hng.tech/hire/linux-developers)
- [PostgreSQL Developers](https://hng.tech/hire/postgresql-developers)

## Conclusion
Completing this task was both challenging and rewarding. It reinforced my understanding of **NGINX, server management, and troubleshooting** in a cloud environment.

🚀 **This is just the beginning of my DevOps journey!** Up next: **Stay tuned!**
