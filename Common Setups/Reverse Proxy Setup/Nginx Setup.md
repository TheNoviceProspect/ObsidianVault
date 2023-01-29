We would want to install nginx with all or most of its modules installed. In my case I have installed via
`sudo apt install nginx-full`

afterwards we just need to create our first reverse proxy host.

`touch /etc/nginx/sites-available/webmin.conf`
`sudo emacs /etc/nginx/sites-available/webmin.conf`

```conf
server {
    server_name webmin.games.tnp.me.uk;
    listen 80;
    location / {
        proxy_pass       http://<some_internal_ip>:10000;
        proxy_set_header   Host             $http_host;
        proxy_set_header   X-Real-IP        $remote_addr;
        proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
    }
}
```

Now lets enable and start our reverse proxy

`sudo systemctl enable --now nginx.service`

now you can even go and follow the [[Common Setups/Reverse Proxy Setup/SSL Setup]]

after that you can expect to wait a few minutes for the SSL certificates to propagate, but should be able to visit:
https://webmin.games.tnp.me.uk

(Please be aware that certain services will require changes on their end to detect this ip redirect)
(Webmin specifically requires you to set `trust_real_ip=1` in `/etc/webmin/miniserv.conf`)