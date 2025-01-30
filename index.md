# NGINX Web Server Setup: My DevOps Stage 0 Journey

## Introduction

As a DevOps engineer I wanted to get some hands on experience with web server configuration. Setting up an NGINX web server on a fresh Ubuntu instance seemed like the perfect challenge. 

In this post I’ll walk you through my approach, the problems I hit, how I fixed them and my learnings.

---

## Task

The task was to:

- Install and configure NGINX on an Ubuntu server.

- Serve a custom HTML page at **/var/www/html/index.html** with:

**"Welcome to DevOps Stage 0 - Makanju Favour/Fave"**

- Make the webpage accessible via the public IP of the server.


---

## How I did it

### Step 1: Create a Cloud Server

For this setup I used an AWS EC2 instance (t2.micro, Ubuntu 24.04). The instance was launched with:

- **OS:** Ubuntu 24.04 LTS  
- **Security Group:** Allowed HTTP (port 80) and SSH (port 22)  
- **Key Pair:** Used for SSH access 

### Step 2: Install and Start NGINX

Once inside the server via SSH I updated the package lists and installed NGINX:

```bash
sudo apt update && sudo apt install -y nginx
```

After installation I started and enabled NGINX so it runs on boot:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

To verify it was running I checked the status:

```bash
sudo systemctl status nginx
```


The output showed NGINX was active and running.

### Step 3: Create the Custom HTML Page

To serve my webpage I created the index.html file in the NGINX document root:

```bash
sudo nano /var/www/html/index.html
```

I added the content:


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

After saving and exiting (CTRL + X, then Y, then Enter) I made sure NGINX could read the file:

```bash
sudo chmod 644 /var/www/html/index.html
```


### Step 4: Restart NGINX

To apply the changes I restarted NGINX:

```bash
sudo systemctl restart nginx
```


I also checked the configuration for syntax errors:

```bash
sudo nginx -t
```


### Step 5: Access the Web Page

Then I entered `http://<my-server-ip>/` in my browser 

and saw:

**"Welcome to DevOps Stage 0 - Makanju Favour/Fave"**

Success! 🎉

---

## Challenges Faced and Solutions

### 1. `index.html` Not Found Error

At first I got a `404 Not Found` error when trying to load the webpage.

**Solution:** I found out that the default file was named `index.nginx-debian.html` instead of `index.html`. I fixed this by renaming it:


```bash
sudo mv /var/www/html/index.nginx-debian.html /var/www/html/index.html
```

Then I edited it:


```bash
sudo vim /var/www/html/index.html
```


## Conclusion

I gained skills in:

- NGINX web server configuration.

- Linux server management on Ubuntu.

- AWS EC2 instance deployment.

- Server and network troubleshooting.

As a DevSecOps and Cybersecurity professional, web server setup is a must know. This hands on will be useful when working with CI/CD automation, infrastructure as code (IaC) and security hardening in cloud.

---

## References

Check out these resources for more info:

- [DevOps Engineers](https://hng.tech/hire/devops-engineers)

- [Cloud Engineers](https://hng.tech/hire/cloud-engineers)

## Conclusion

This was engaging and fun. I learned more about **NGINX, server management and troubleshooting in cloud**

🚀 Next up: **Stay tuned**

