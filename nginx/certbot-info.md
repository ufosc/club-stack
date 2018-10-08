# Certbot Info

We are using the free LetsEncrypt service to get an SSL certificate (so our site can use https). They provide a program called Certbot to automatically set up and renew the certificates. The below instructions are used for the initial set up and renewal process.

## Set Up

```bash
docker run -it --rm \
      -v certs:/etc/letsencrypt \
      -v certs-data:/data/letsencrypt \
      deliverous/certbot \
      certonly \
      --webroot --webroot-path=/data/letsencrypt \
      -d ufopensource.club -d www.ufopensource.club
```

## Renewal

Use a cron job with

```bash
0 0 */15 * * docker run -t --rm -v certs:/etc/letsencrypt -v certs-data:/data/letsencrypt -v /var/log/letsencrypt:/var/log/letsencrypt deliverous/certbot renew --webroot --webroot-path=/data/letsencrypt && docker kill -s HUP nginx >/dev/null 2>&1
```

## Resources

- [Blog on the subject](https://miki725.github.io/docker/crypto/2017/01/29/docker+nginx+letsencrypt.html)
- [Official Certbot Docs](https://certbot.eff.org/docs/install.html#running-with-docker)