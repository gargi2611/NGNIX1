# NGNIX1
To add the videos from local machine to remote VPS use this command before login is must

```bash
scp -r /local/path/to/test(local directory path) root@195.35.21.226:/var/www/html/ (remote directory path)
```

Login
```bash 
ssh root@195.35.21.226
```

enter password


compression of videos through ffmpeg

```bash
ffmpeg -i input.mp4 -b:v 3000k -s 1920x1080 -c:a aac -strict -2 output-1080p.mp4
ffmpeg -i input.mp4 -b:v 1500k -s 1280x720 -c:a aac -strict -2 output-720p.mp4
ffmpeg -i input.mp4 -b:v 800k -s 854x480 -c:a aac -strict -2 output-480p.mp4

```

open the config file

```bash
sudo nano /etc/nginx/sites-available/default
```


add code to the config file

```bash
server {
    listen 8081 default_server;
    listen [::]:8081 default_server;

    root /var/www/html/test;  # Updated directory path  #root /home/root/test;

    index index.html index.htm index.nginx-debian.html;

    server_name _;

    location / {
        try_files $uri $uri/ =404;
    }

    # Serve videos from the /videos/ URL
    location /videos/ {
        alias /var/www/html/test/;  # Updated directory path
    }
}" show error even the format is correct


# Existing Codecolor Website Configuration
server {
    listen 80;
    server_name www.codecolor.online;
    
    root /var/www/codecolor;
    index index.html index.htm;
    
    location / {
        try_files $uri $uri/ =404;
    }

    # Additional configurations (SSL, proxy_pass, etc.) if any...
}

# New Video Hosting Website Configuration
server {
    listen 80;
    server_name www.videoplatform.online;

    root /var/www/videoplatform;
    index index.html index.htm;

    # Serve video files efficiently
    location /videos/ {
        root /var/www/videoplatform;
        # Ensure proper MIME types for video
        types {
            video/mp4 mp4;
            video/webm webm;
            video/ogg ogg;
        }
        expires max;
        add_header Cache-Control "public";
    }

    # Handle other requests
    location / {
        try_files $uri $uri/ =404;
    }

    # Additional configurations like rate limiting
    location /videos/ {
        limit_rate_after 10m;
        limit_rate 1m;
    }
}
```
for permission 


```bash

chmod 644 /path/to/remote/file.mp4
```


use to restart ngnix

```bash
systemctl restart nginx
```
