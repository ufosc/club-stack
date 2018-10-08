# Initial server setup

## Set SSH Keys only

In `/etc/ssh/sshd_config`, set:
- "PermitRootLogin" to "no"
- "PubkeyAuthentication" to "yes"
- "PasswordAuthentication" to "no"

Then update the config `systemctl restart ssh`

## Setup firewall

```bash
ufw allow http
ufw allow https
ufw allow OpenSSH
```

```bash
ufw enable
```

## Create project group

This group will be for people who can modify the production projects 

```bash
groupadd project
```

Then created folder for projects
```bash
sudo chgrp -R project /project/
sudo chmod -R 2775 /project/
```

## Install docker

Using the official documentation
- [Docker install](https://docs.docker.com/install/linux/docker-ce/ubuntu/#upgrade-docker-after-using-the-convenience-script)
- [Docker post install](https://docs.docker.com/install/linux/linux-postinstall/)
- [Docker compose](https://docs.docker.com/compose/install/)