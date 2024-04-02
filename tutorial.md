
## what we will do in this tutorial:
going from a fresh Arch Linux server running on DigitalOcean to serving the content in the html file on the web


## Step 1: how to create a DigitalOcean Droplet
1. log into your digital ocean account, 
2. click the green Create button in the top right to open the create menu.
3. In the create menu, click Droplets to open the Droplet create page. If you don’t have any Droplets, the Resources tab displays a large, blue Get Started with a Droplet button, which takes you to the same Droplet create page.
In the Choose Region section, select the region where you want to create your Droplet. (use san 3)
4. In the Choose an image section, you choose the image to use for your Droplet
5. choose the "basic droplet" pan
6. In the Choose Authentication Method section, choose SSH key.
7. do the rest as the instructed and create the droplet


## Step 2: how to connect to the Server via SSH and make neccessary files:
use  ssh -i .\.ssh\do-key username@your-droplet-ipaddress
the type: mkdir -p /web/html/nginx-2420
then: cd /web/html/nginx-2420



## Step 3: Installing Nginx
type: sudo pacman -Sy vim nginx


## Step 4: Configuring Nginx
type: 
sudo vim nginx-2420.conf
and in there type:
server {
    listen 80;
    server_name your_domain.com;

    root /web/html/nginx-2420;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}

## step 5: 
create a index.html file and put this into it:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2420</title>
    <style>
        * {
            color: #db4b4b;
            background: #16161e;
        }
        body {
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }
        h1 {
            text-align: center;
            font-family: sans-serif;
        }
    </style>
</head>
<body>
    <h1>All your base are belong to us</h1>
</body>
</html>

