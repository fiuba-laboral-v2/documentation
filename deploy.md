# Apache
I installed and set up apache following this [instructions](https://www.digitalocean.com/community/tutorials/como-instalar-el-servidor-web-apache-en-ubuntu-18-04-es): 
## Set up
### Install apache
* `sudo apt update`
* `sudo apt install apache2`
### Allow port 80 for unencrypted web traffic
* `sudo ufw allow 'Apache'`
* `sudo ufw enable`
### Create folder to serve html and we give ourselves user permission
* `sudo mkdir -p /var/www/laboral-v2.fi.uba.ar/html`
* `sudo chown -R $USER:$USER /var/www/laboral-v2.fi.uba.ar/html`
* `sudo chmod -R 755 /var/www/laboral-v2.fi.uba.ar`
* `nano /var/www/laboral-v2.fi.uba.ar/html/index.html` -> load html here
### Set default settings:
  * `sudo nano /etc/apache2/sites-available/laboral-v2.fi.uba.ar.conf`

Write the following: 
``` 
<VirtualHost *:80>
    ProxyPass /laboral-api http://localhost:5000
    ServerAdmin admin@$HOSTNAME
    ServerName $HOSTNAME
    ServerAlias www.$HOSTNAME
    DocumentRoot /var/www/html
    Alias "/laboral" $SERVED_HTML_PATH
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
* `sudo a2ensite "$HOSTNAME.conf"`  
Where HOSTNAME is the name of the host that will be written in the browser when using the application.  

* `sudo a2enmod proxy`
* `sudo a2enmod proxy_http`
* `sudo systemctl restart apache2`

## Useful commands:
* List the application profiles inside ufw by typing: `sudo ufw app list`
* Verify web server: `sudo systemctl status apache2`
* Returns some addresses separated by spaces: `hostname -I`
* Returns the public IP address in the way it is perceived from an external place on the internet: `curl -4 icanhazip.com`
* Stop your web server: `sudo systemctl stop apache2`
* Start your web server: `sudo systemctl start apache2`
* Stop and restart your web server: `sudo systemctl restart apache2`
* Recharge Apache: `sudo systemctl reload apache2`
* Deshabilitar : `sudo systemctl disabled apache2`
* Habilitar : `sudo systemctl enabled apache2`
# Travis
The following instructions were based using this [guide](https://github.com/dwyl/learn-travis/blob/master/encrypted-ssh-keys-deployment.md)
## Create unencrypted key for deployment
### Log-in to Your Server Instance
```
ssh user@ip.add.ress.here
```
### Create a new SSH Key
```
cd ~/.ssh
ssh-keygen -t rsa -b 4096 -C "TravisCIDeployKey"
```
### Add the new SSH Key to the authorized_keys File
```
cat id_rsa.pub >> authorized_keys
```
### Securely Download the SSH Key
* On your repository: 
```
echo "deploy_key" >> .gitignore
```
* `scp user@ip.add.ress.here:/root/.ssh/id_rsa  ./deploy_key`
### Install Travis-CI CLI
```
gem install travis
```
### Login to travis pro (endpoint .com)
```
travis login --pro
```
### Encrypt the Private Key
```
touch .travis.yml && travis encrypt-file ./deploy_key --add
```
Push the generated `deploy_key.enc` to your repository
### Add te folowing to your travis.yml file
```
before_install:
- openssl aes-256-cbc -K $encrypted_<number>_key -iv $encrypted_<number>_iv
  -in deploy_key.enc -out ./deploy_key -d
- eval "$(ssh-agent -s)"
- chmod 600 ./deploy_key
- echo -e "Host $SERVER_IP_ADDRESS\n\tStrictHostKeyChecking no\n" >> ~/.ssh/config
- ssh-add ./deploy_key
```
Where the number of $encrypted_<number>_key and $encrypted_<number>_iv can be found in the enviroment variables in the setting of your repo in travis.