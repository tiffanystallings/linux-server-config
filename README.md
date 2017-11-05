# Configure a Linux Server
Basic access information on where to find my item database server.

## IP Address and Port
The server is located at:
52.205.178.202 SSH Port: 2200

## URL
[http://52.205.178.202/](http://52.205.178.202/)

## Summary of Changes
I began by running:
`sudo apt-get update`
and:
`sudo apt-get upgrade`
To bring the server up to date.

I then created two new users:
`sudo adduser tiffany`
and:
`sudo adduser grader`

I needed these users to have sudo powers, so I added files for each of them in the /etc/sudoers.d.
These files say:
`tiffany ALL=(ALL) NOPASSWD:ALL`
and:
`grader ALL=(ALL) NOPASSWD:ALL`

For each user, I create an authorized keys file in the .ssh folder for each user. This file contains the public key for those users.

I next needed to alter the SSH port by configuring the `etc/ssh/sshd_config` file.

I needed to alter the UFW to match the new port.
`sudo ufw default deny incoming`

`sudo ufw default allow outgoing`

`sudo ufw allow 2200/tcp`

`sudo ufw allow ntp`

`sudo ufw allow www`

`sudo ufw enable`

At this point my server is configured and ready to go. Python and Git came already installed on the Lightsail server, so I just needed to install my other modules and sqlite3 -- the database my item catalog was built on.

`sudo apt-get install sqlite3`

I was also going to need Apache and mod-wsgi.

`sudo apt-get install apache2`

`sudo apt-get install mod-wsgi`

I configured my Apache server to run the myapp.wsgi file set up to start up my flask application.
Next, I needed my python modules.

`sudo apt-get install python-pip`

`pip install flask-sqlalchemy`

`pip install flask`

`pip install requests`

At this point I was able to clone my item catalog repository onto the server. From there, it was just a few tweaks to the item catalog itself to get it up and running smoothly on the server.

## Third Party Resources
* Amazon Lightsail
* Ubuntu
* Python 2
* SQLite
* Flask-SQLAlchemy
* Apache HTTP Server
* Mod WSGI
* Git

