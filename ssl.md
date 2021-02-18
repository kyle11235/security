
# ssl

https://certbot.eff.org/lets-encrypt/pip-nginx (nginx + other unix, do not recommand use docker)

- start nginx, refer to nginx/README.md
- A record, www.example.com -> ip (Welcome to nginx on Fedora!)
- install certbot-auto

        wget https://dl.eff.org/certbot-auto
        mv certbot-auto /usr/local/bin/certbot-auto
        chown root /usr/local/bin/certbot-auto
        chmod 0755 /usr/local/bin/certbot-auto

- create certificate

        /usr/local/bin/certbot-auto --nginx (interactive command, get a certificate and have Certbot edit your Nginx configuration)

        xx@xx.com (urgent contact email)
        www.example.com (nginx doesn't support *.example.com)
        choose enable redirect from http to https

- auto renew certificate

        Congratulations! Your certificate and chain have been saved at:
        /etc/letsencrypt/live/www.example.com/fullchain.pem
        Your key file has been saved at:
        /etc/letsencrypt/live/www.example.com/privkey.pem
        Your cert will expire on 2019-11-21. To obtain a new or tweaked
        version of this certificate in the future, simply run certbot-auto
        again with the "certonly" option. To non-interactively renew *all*
        of your certificates, run "certbot-auto renew"

        echo "0 0,12 * * * root python -c 'import random; import time; time.sleep(random.random() * 3600)' && /usr/local/bin/certbot-auto renew" | tee -a /etc/crontab > /dev/null

        certs with version are archived to /etc/letsencrypt/archive/www.example.com/  (cert1.pem  chain1.pem  fullchain1.pem  privkey1.pem)
