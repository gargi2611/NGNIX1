login to the root user

```bash
ssh root@195.35.21.226
```

check directory

```bash
ls
```

video directory folder

```bash
 cd /var/www/html/videos/
```

always use this command before the login to add the videos to the remote machine (VPS or VPC) 

```bash
 scp "F:/Paarsh Infotech/learn-main/learn-main/chatgpt.mp4"
```

re login

```bash
ssh root@195.35.21.226
```


check for the videos are visible or not

```bash
 ls /var/www/html/videos/
```

port changing and server configuration

 ```bash
sudo nano /etc/nginx/sites-available/default
```

checking for the working port

```bash
netstat -tuln
```

checking for the syntax of the configuration file

```bash
 sudo nginx -t
```

restart the nginx 

```bash
sudo systemctl restart nginx
sudo systemctl reload nginx
```

check for the ip working

```bash
ping 195.35.21.226
```

check for the firewall resolution
```bash
 sudo chmod -R 755 /var/www/html/videos
sudo ufw status
```

firewall rule updation for the port
```bash
sudo ufw allow 8090
sudo ufw reload
```


```bash
sudo ufw status
```
check the status ofthe config file 

```bash
sudo nginx -t
```


```bash
sudo systemctl restart nginx
```



```bash
 sudo chmod -R 755 /var/www/html/videos
sudo chown -R www-data:www-data /var/www/html/videos
```

online browser video checking
```bash
http://195.35.21.226:8090/placement.mp4
```

ffmeg video resolutions

```bash
root@srv449457:~# cd /var/www/html/videos
root@srv449457:/var/www/html/videos# ffmpeg -i chatgpt.mp4 -b:v 3000k -s 1920x1080 -c:a aac -strict -2 chatgpt-1080p.mp4
ffmpeg -i chatgpt.mp4 -b:v 1500k -s 1280x720 -c:a aac -strict -2 chatgpt-720p.mp4
ffmpeg -i chatgpt.mp4 -b:v 800k -s 854x480 -c:a aac -strict -2 chatgpt-480p.mp4
```

check for the videos are visible in the directory or not

```bash
 ls -lh
```


```bash

```


```bash

```
