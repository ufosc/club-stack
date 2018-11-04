# Certbot Info

We are using the free LetsEncrypt service to get an SSL certificate (so our site can use https). They provide a program called Certbot to automatically set up and renew the certificates. The below instructions are used for the initial set up and renewal process.

## Set Up

Add the package repository and install Certbot

```bash
sudo add-apt-repository ppa:certbot/certbot
sudo apt update
sudo apt install python-certbot-nginx
```

The initial setup (note: we are passing in `/var/www/ufopensource` and `/etc/letsencrypt/ufopensource` as a volume to the Nginx Docker container so Certbot's work can be seen):

```bash
sudo certbot certonly --webroot -w /var/www/ufopensource -d ufopensource.club -d www.ufopensource.club 
```

## Renewal

The package installed above should automatically renew the certificate as long as the server config is valid.

Renewal can be tested with the following command:

```bash
sudo certbot renew --dry-run
```

## Resources

- [Certbot usage](https://certbot.eff.org/lets-encrypt/ubuntubionic-other)
- [Non-docker Nginx and Certbot walkthrough](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-18-04)
- [Certbot automatic renewal](https://certbot.eff.org/docs/using.html#automated-renewals)