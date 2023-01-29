We would want to install nginx with all or most of its modules installed. In my case I have installed via
`sudo apt install nginx-full`

afterwards we just need to create our first reverse proxy host.

`touch /etc/nginx/sites-available/example.com`
`sudo emacs /etc/nginx/sites-available/example.com`

```conf
server {
    server_name example.com;
    listen 80;
    location / {
        proxy_pass       http://127.0.0.1:8080;
        proxy_set_header   Host             $http_host;
        proxy_set_header   X-Real-IP        $remote_addr;
        proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
    }
}
```

Now lets enable and start our reverse proxy

`sudo systemctl enable --now nginx.service`

now you can even go and follow the [[Common Setups/Reverse Proxy Setup/SSL Setup]]![[]]