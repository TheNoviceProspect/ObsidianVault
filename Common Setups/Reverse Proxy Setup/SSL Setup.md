Install free ssl certificates from certbot
`sudo apt install certbot python3-certbot-nginx`

then issue your first certificate against an nginx vhost:

`sudo certbot --nginx -d host.domain.tld`
obviously filling in your hostname