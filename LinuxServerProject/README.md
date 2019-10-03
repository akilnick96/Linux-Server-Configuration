Linux Server Configuration

IP address:- 13.232.15.177

Software Installed:-
1.Python 2.7.12
2.pip 8.1.1
3.sqlite3 3.11.0

Steps to configure:-
1.To change the port from 22 to 2200 do the following steps:-
   Go to /etc/ssh/sshd_config and add the Port 2200 below Port 22.
   Add a custom port in the firewall settings of lightsail.
   Then run the following commands.
   
  $ sudo ufw status

  $ sudo ufw default deny incoming

  $ sudo ufw default allow outgoing

  $ sudo ufw allow ssh

  $ sudo ufw allow 2200/tcp

  $ sudo ufw allow www

  $ sudo ufw enable

  $ sudo ufw status
  
  Then check if the instance can be connected through the local machine using 
    $ ssh -i .ssh/<your_private_key> <your_username>@<your_public_IP> -p 2200
    Then remove the Port 22 from sshd_config and Firewall settings.
    
Steps to run Flask app:-
1. sudo apt-update
2. sudo apt-upgrade
3. To get WSGI, run 
    sudo apt-get install libapache2-mod-wsgi
4. Once we have that, we need to make sure we've enabled WSGI
    sudo a2enmod wsgi
5. To setup a Flask environment
    cd /var/www/
    mkdir Item-Catalog
6. Use git clone to copy your FlaskApp onto the instance and have it under a dir 'FlaskApp'
7. Set up python-pip and imports needed
    apt-get install python-pip
    pip install Flask
    pip install requests
    pip install sqlalchemy
8. Set up a Flask config file:
    nano /etc/apache2/sites-available/CatalogApp.conf
9. Run
    sudo a2ensite FlaskApp
    service apache2 reload
10. Go to /var/www/Item-Catalog and configure WSGI file
11. Then run service apache2 restart

Reference:-
1.https://pythonprogramming.net/creating-first-flask-web-app/
2.https://knowledge.udacity.com/questions/19521
3.https://knowledge.udacity.com/questions/42106
4.https://flask.palletsprojects.com/en/1.1.x/installation/
5.https://stackoverflow.com/questions/4636970/sqlite3-operationalerror-unable-to-open-database-file
6.https://stackoverflow.com/questions/7670289/sqlite3-operationalerror-unable-to-open-database-file/7670618
