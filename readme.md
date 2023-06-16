Slightly modified version of Tinyfilemanager for use on a Raspberry Pi during the 
Hackers & Designers Summer Camp 2023. 
The script looks for a `index.css` in each directory and will use that for styling
that view. Yes, it's going to be messy. 

See the readme.md in the Tinyfilemanager directory for setup & configuration. 

Docker compose only works on 64-bit Raspbian, so make sure that's installed. 

The original Docker setup in Tinyfilemanager didn't work so it set it following this tutorial:
https://blog.devsense.com/2019/php-nginx-docker

To get `docker-compose` on the raspberry I followed this tutorial:
https://jfrog.com/connect/post/install-docker-compose-on-raspberry-pi/

To start run 
`docker-compose up -d --build`

The `restart:always` directives in docker-compose.yml should make sure
that the server restarts then the Pi does. 
Make sure Docker starts with `sudo systemctl start docker`.

The line `- ./nginx-config/default.conf:/etc/nginx/conf.d/default.conf` maps
an external hd connected to the Raspberry pi to the docker instance and the
filemanager uses that directory for storage.