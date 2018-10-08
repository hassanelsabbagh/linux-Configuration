# linux-Configuration

**IP-Address**: 35.159.15.176
**SSH-Port**:  2200
**URL**: http://35.159.15.176/


## Software Installed

`sudo apt-get install apache2` to install apache2


`sudo apt-get install postgreql` to install postgresql

`sudo apt-get install python-psycopg2`
`sudo apt-get install python-flask`
`sudo apt-get install python-sqlalchemy`

`sudo apt-get install git` to install git


## configuration changes made

### update all currently installed packages

`sudo apt-get update`
`sudo apt-get upgrade`


### Change the SSH port from 22 to 2200

`sudo nano /etc/ssh/sshd_config` and change the port number from 22 to 2200


### Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123)

`sudo ufw allow 2200/tcp`
`sudo ufw allow 80/tcp`
`sudo ufw allow 123/udp`
`sudo ufw enable`


### Give grader access

`sudo adduser grader` to creare user `grader` and then `sudo nano /etc/sudoers.d/grader` and type `grader ALL=(ALL) NOPASSWD:ALL`
then generete SSH key pair:
1.`ssh-keygen`
2.`ssh-copy-id -i ~/.ssh/grader grader@35.159.15.176 -p 2200`
3.`ssh -i ~/.ssh/grader grader@35.159.15.176 -p 2200` to login to server


### Configure the local timezone to UTC

`sudo dpkg-reconfigure tzdata`

-then Install and configure Apache to serve a Python mod_wsgi application from the command above


### Install and configure PostgreSQL

1.Install postgresql from the command above

2.`sudo nano /etc/postgresql/9.3/main/pg_hba.conf` to not allow remote connections

3.1.`sudo su - postgres` 
3.2.`psql`
3.3.`CREATE DATABASE catalog`

4.install `git` from the command above

### Deploy catalogItem

`git clone https://github.com/hassanziku/CatalogItem.git` to clone the project to the VM

### Third-Party Resources

[DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps)
[StackOverflow](https://stackoverflow.com)
