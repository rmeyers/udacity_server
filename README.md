# udacity_server

## IP Address and SSH Port

Public IP: 18.216.120.52
SSH Port: 2200

## URL to hosted web app

This is incomplete. I thought it would show up here: http://18.216.120.52/, but I keep getting an error. I've worked on this for some time and am hoping you might be able to help me a little bit with it.

## Summary of software installed and configured changes made

1. Used Amazon Lightsail to get a server going. 
2. SSH'd into the server on my local machine. 
3. Created a new user 'ryan', and another user 'grader'. 
4. Used local ssh-keygen to create keys for both accounts. Added them to their own .ssh folders. Basically, I followed the steps 1-6 from here: https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04. 
5. Updated packages using `sudo apt-get update` followed by `sudo apt-get upgrade`.
6. Set up firewall using the following commands: 
`sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw allow 2200/tcp (Note: Changed SSH above to port 2200)
sudo ufw allow www
sudo ufw allow 123/udp
sudo ufw enable`
7. Configured timezone using: `dpkg-reconfigure tzdata`
8. Installed Apache2: `sudo apt-get install apache2`
9. Installed Python mod_wsgi: `sudo apt-get install libapache2-mod-wsgi`
10. Here, I created an example wsgi file and ran a simple "Hello World" app to confirm that Apache2 and wsgi were working properly. This worked, they were working. 
11. Installed Postgres and created a new DB. 
12. The user is "postgres". Password in my notes to you. 
13. Installed Git and copied over my backend-final (catalog) project. 
14. Added .htaccess file at root of project directory with `RedirectMatch 404 /\.git`
15. Installed Pip and Virtual Environment:
`sudo apt-get install python-pip
sudo pip install virtualenv`
16. Installed all requirements using: `pip install -r requirements.txt`
17. Tested that the app was running by going to directory for catalog and running `python __init__.py` - running properly. 
18. Configured virtual host in Apache2: `sudo nano /etc/apache2/sites-available/catalog.conf`
19. Enabled virtual host: `sudo a2ensite catalog`
20. Created and configured the WSGI file in the top of the catalog directory: `catalog.wsgi`
21. Replaced sqlite references with postgresql: `engine = create_engine('postgresql://catalog:catalog@localhost/catalog')`
22. Added Lightsail server IP to hosts file: `sudo nano /etc/hosts`
23. Removed 000-default.conf file from Apache2
24. Restarted Apache: `sudo service apache2 restart`
25. Restarted Python app: `sudo python __init__.py`


## List of third-party resources

https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
https://stackoverflow.com/questions/6142437/make-git-directory-web-inaccessible
https://www.knownhost.com/wiki/security/misc/how-can-i-change-my-ssh-port
https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04
https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-an-ubuntu-14-04-vps
https://help.ubuntu.com/lts/serverguide/firewall.html

### Author

Ryan Meyers

