# 1. Update Debian

Update your system with the following commands:

```bash
sudo apt-get update && sudo apt-get upgrade -y
```

## 2. Install Required Components

Download and install Tomcat 9.0.50:

```bash

wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.50/bin/apache-tomcat-9.0.50.tar.gz
sudo tar xvf apache-tomcat-9.0.50.tar.gz -C /opt/
sudo mv /opt/apache-tomcat-9.0.50 /opt/tomcat

```

Install MongoDB, PostgreSQL, and Redis:

```bash

sudo apt-get install -y mongodb
sudo apt-get install -y postgresql
sudo apt-get install -y redis-server

```

## 3. Configure Environment Variables

Update the `.env` file in your project with the following content:

```bash

POSTGRES_DB=database
POSTGRES_USER=myuser
POSTGRES_PASSWORD=password
MONGO_INITDB_DATABASE=database
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
REDIS_PORT=6379

```

## 4. Set Up Tomcat

Edit the `tomcat-users.xml` file to create a user with full rights:

```bash

sudo nano /opt/tomcat/conf/tomcat-users.xml

```

Add the following lines:

```xml

<role rolename="manager-gui"/>
<role rolename="admin-gui"/>
<user username="admin" password="your_password" roles="manager-gui,admin-gui"/>

```

## 5. Deploy WAR File

Remove the `ROOT` folder and deploy the WAR file:

```bash

sudo rm -rf /opt/tomcat/webapps/ROOT
sudo cp /path/to/your/project.war /opt/tomcat/webapps/ROOT.war
sudo /opt/tomcat/bin/shutdown.sh
sudo /opt/tomcat/bin/startup.sh

```

## 6. Restart Services

Restart all services to apply changes:

```bash

sudo /opt/tomcat/bin/shutdown.sh
sudo /opt/tomcat/bin/startup.sh
sudo systemctl restart mongodb
sudo systemctl restart postgresql
sudo systemctl restart redis-server

```

## 7. Verify Deployment

Check the application by navigating to `http://localhost:8080` in your web browser.
