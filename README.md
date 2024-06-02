# NGINX Reverse Proxy Config files
These files are the NGINX config files used in my YouTube video to set up NGINX as a reverse proxy in order to apply SSL encryption and certificate-based authentication for my internal websites.

## NGINX Config file
nginx.conf contains the full configuration for my specific case whereby I'm using NGINX to proxy access to my weatherstation and webcam.

More info on config options:
proxy_pass  <--<< This is used to define where the requests are sent to 
proxy_buffering <--<< Turning this off results in data being sent straight to the client as it's received from the server. Otherwise it gets buffered internally before being returned
proxy_set_header Host $http_host <--<< If a host were defined in the incoming request (i.e. it came from another website as opposed to a browser) then this value is passed through to the target
proxy_set_header X-Real-IP $remote_addr <--<< This tells the remote web server who made teh original request
proxy_set_header X-Forwarded-For <--<< Just a varient of the above saying who we're proxying on behalf of
proxy_set_header X-Forwarded-Proto <--<< The protocol used in the orginal request

## NGINX Docker-Compose file
nginx.yaml is a docker-compose configuration file that can be used to run the NGINX server using the config above and certificates generated using the scripts in https://github.com/jeffspiinthesky/pki
