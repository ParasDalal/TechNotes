Add SSH Key


# nginx

```conf
##GridPane_Prometheus_vHost_Begin##
#HTTPS#
## Do not edit directly.
## All changes will be lost.
## Please use a location specific
## include to customise your config

include /var/www/gujarati.dev/nginx/*-http-context.conf;
server {
    listen 80;
    listen [::]:80;
 
    server_name gujarati.dev www.gujarati.dev;
 
    #include /var/www/gujarati.dev/nginx/gujarati.dev-headers-csp.conf;
    include /etc/nginx/common/headers-http.conf;
    include /var/www/gujarati.dev/nginx/*-return-https-context.conf;

    return 301 https://$host$request_uri;
}
 
server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
 
    server_name gujarati.dev www.gujarati.dev;

    ssl_certificate /etc/letsencrypt/live/gujarati.dev/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/gujarati.dev/privkey.pem;
    ssl_stapling_file /etc/nginx/ocsp/gujarati.dev.resp;
    ssl_trusted_certificate /etc/letsencrypt/live/gujarati.dev/chain.pem;

    access_log /var/log/nginx/gujarati.dev.access.log we_log;
    error_log /var/log/nginx/gujarati.dev.error.log;

    location / {
        proxy_set_header        Host $host;
        proxy_set_header        X-Real-IP $remote_addr;
        proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for; aio threads;
        proxy_set_header        X-Forwarded-Proto $scheme;

        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "Upgrade"; 
        
        proxy_pass http://0.0.0.0:5000;
    }

    #root /var/www/gujarati.dev/htdocs;
    #index index.php index.html index.htm;

    #include /etc/nginx/common/acl.conf;
    #include /etc/nginx/common/7g.conf;
    #include /etc/nginx/common/6g.conf;
    include /var/www/gujarati.dev/nginx/*gujarati.dev-sockfile.conf;
    include /etc/nginx/common/gujarati.dev-compression.conf;
    include /var/www/gujarati.dev/nginx/*-realip-context.conf;
    include /etc/nginx/common/gridpane-realip.conf;
    #include /var/www/gujarati.dev/nginx/gujarati.dev-headers-csp.conf;
    include /etc/nginx/common/headers-http.conf;
    include /etc/nginx/common/headers-https.conf;
    include /etc/nginx/common/headers-html.conf;
    include /var/www/gujarati.dev/nginx/*-main-gujarati.dev-context.conf;
    include /var/www/gujarati.dev/nginx/*-main-context.conf;
    include /etc/nginx/extra.d/*main-context.conf;
    #include /etc/nginx/common/gujarati.dev-sitemap.conf;
    #include /etc/nginx/common/gujarati.dev-static.conf;
    #include /etc/nginx/common/gujarati.dev-wpcommon.conf;
    #include /etc/nginx/common/gujarati.dev-php.conf;
    #include /etc/nginx/common/wpsubdir.conf;
    #include /etc/nginx/common/security.conf;
}
 
##GridPane_Prometheus_vHost_End##
```

## SSL

```sh
sudo certbot certonly --nginx -d gujarati.dev -d www.gujarati.dev
service nginx force-reload

sudo certbot renew --dry-run
```

Remember to create `.well-known/acme-challenge` folder in the web root

## Logs

```
Requesting a certificate for gujarati.dev and www.gujarati.dev
Successfully received certificate.

Certificate is saved at: /etc/letsencrypt/live/gujarati.dev/fullchain.pem
Key is saved at:         /etc/letsencrypt/live/gujarati.dev/privkey.pem

This certificate expires on 2023-04-17.
These files will be updated when the certificate renews.
Certbot has set up a scheduled task to automatically renew this certificate in the background.
```



## Kavita

Logins:
admin / readme2023
demo / demo123

```
Run Kavita in background:
first time: screen -S kavita
./opt/kavita/Kavita
detach with Ctrl+A, then D

reattach later with: screen -r kavita

temporary reverse proxy - ngrok http 5000 --subdomain=kavita
```

## SystemD
```
[Unit]
Description=Kavita
After=network.target

[Service]
User=root
Group=root
Type=simple
WorkingDirectory=/opt/kavita
ExecStart=/opt/kavita/Kavita
TimeoutStopSec=30
KillMode=process
Restart=on-failure

[Install]
WantedBy=multi-user.target
```