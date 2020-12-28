# SSL certifikát Buypass přes certbot

https://community.buypass.com/t/k9r5cx/get-started

1. `certbot register -m 'YOUR_EMAIL' --agree-tos --server 'https://api.buypass.com/acme/directory'`
1. `certbot --nginx -d example.com -d www.example.com --server 'https://api.buypass.com/acme/directory'`
