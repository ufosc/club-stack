# Common Server Commands

## How to add a user

1. Make user without password
	```bash
	sudo useradd -m -s /bin/bash <username>
	sudo passwd -e <username>
	```
2. Copy over their public ssh key
	```bash
	sudo mkdir /home/<username>/.ssh
	sudo nano /home/<username>/.ssh/authorized_keys
	```
3. Set correct permissions
	```bash
	sudo chmod -R go= /home/<username>/.ssh
	sudo chown -R <username>:<username> /home/<username>/.ssh/
	```

4. (Optional) Add the user to a group
	```bash
	sudo usermod -aG <groupname> <username>
	```

## Change user password

As a user
```bash
passwd 
```

As sudo
```bash
sudo passwd <username>
```
and then fill out password prompt