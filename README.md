# linux-apache-virtual-host-setup
A guide to setting up several Virtual Hosts in Apache on Linux, allowing you to host and serve multiple PHP applications on different ports.

---

## Prerequisites
Before you begin, ensure you have:
- A Linux server with Apache installed.

---

## Steps to Configure Virtual Hosts

### Step 1: Create Directories for Each Application
Create directories to hold the files for each application:

```bash
sudo mkdir /var/www/html/app1
sudo mkdir /var/www/html/app2
sudo mkdir /var/www/html/app3
```

### Step 2: Create Configuration Files for Each Virtual Host
Create a configuration file for each application:

```bash
sudo nano /etc/apache2/sites-available/app1.conf
```
Then Past the following code in the config file you created:

```bash
<VirtualHost *:8081>
    DocumentRoot /var/www/html/app1
    <Directory /var/www/html/app1>
        AllowOverride All
        Require all granted
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/app1_error.log
    CustomLog ${APACHE_LOG_DIR}/app1_access.log combined
</VirtualHost>
```
You can then create a similar config file for the `app2` and `app3`. Remember to change the **ports** and the **directory for Document Root**.

###Step 3: Enable the Virtual Hosts
Enable each Virtual Host with the a2ensite command:

```bash
sudo a2ensite app1.conf
sudo a2ensite app2.conf
sudo a2ensite app3.conf
```
###Step 4: Update Apache to Listen on New Ports
Edit the `ports.conf` file:
```bash
sudo nano /etc/apache2/ports.conf
````
Configure Apache to listen on the required ports:

```bash
Listen 8081
Listen 8082
Listen 8083

````

###Step 5: Reload Apache and Visit the Applications
```bash
sudo systemctl restart apache2
```
Visit the applications in your browser:

`http://your-server-ip:8081`
`http://your-server-ip:8082`
`http://your-server-ip:8083`

Replace `(your-server-ip)` with the actual IP address of your server and you will be able to access each of the PHP apps deployed in VHs.
