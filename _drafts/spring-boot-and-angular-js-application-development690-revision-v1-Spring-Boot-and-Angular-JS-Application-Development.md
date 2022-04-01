---
id: 705
title: 'Spring Boot and Angular JS Application Development'
date: '2021-08-29T02:49:19+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/690-revision-v1/'
permalink: /690-revision-v1/
---

## Installing Environment

```
<pre class="wp-block-code">```
sudo apt update
sudo apt install snapd

sudo apt install -y default-jdk
sudo snap install node --classic
sudo npm install -g @angular/cli --unsafe-perm=true --allow-root

sudo snap install intellij-idea-ultimate --classic --edge
sudo snap install --classic code 
sudo snap install postman

sudo snap install http
```
```

<figure class="wp-block-embed"><div class="wp-block-embed__wrapper">https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-20-04-quickstart </div></figure>## Setup PostgreSQL Database Server

We are going to show how to install PostgreSQL database on a Debian Linux system.

```
<pre class="wp-block-preformatted">$ sudo apt-get install postgresql  
```

Check status

```
<pre class="wp-block-preformatted">$ /etc/init.d/postgresql status
```

Add password for the postgress account

```
<pre class="wp-block-preformatted">$ sudo -u postgres psql postgres
psql (9.5.10)
Type "help" for help.

postgres=# \password postgres
Enter new password: 
Enter it again: 
```

Create a new user with a password

```
<pre class="wp-block-preformatted">$ sudo -u postgres createuser --interactive --password usertest
Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create databases? (y/n) y
Shall the new role be allowed to create more new roles? (y/n) n
Password: 
```

Create a new database test\_db with the new role as the owner

```
<pre class="wp-block-preformatted">$ sudo -u postgres createdb test_db -O usertest
```

Now edit the `pg_hba.conf` file to enable connection

```
<pre class="wp-block-preformatted">$ sudo vi /etc/postgresql/12/main/pg_hba.conf
```

By changing the lines below with **trust**

```
<pre class="wp-block-preformatted"># "local" is for Unix domain socket connections only
local   all             all                                     trust
# IPv4 local connections:
host    all             all             127.0.0.1/32            trust
```

Restart the server

```
<pre class="wp-block-preformatted">$ sudo service postgresql restart
```

Check if the new role can access the new database

```
<pre class="wp-block-preformatted">$ psql -U user_test -d test_db -W 
```