# Runbook for Deploying 'Class Schedule' on Debian

Update Debian with 
`sudo apt-get update && sudo apt-get upgrade -y`. 
Install Tomcat 9.0.50, MongoDB, PostgreSQL, and Redis with 
`wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.50/bin/apache-tomcat-9.0.50.tar.gz`, 
`sudo tar xvf apache-tomcat-9.0.50.tar.gz -C /opt/`, `sudo mv /opt/apache-tomcat-9.0.50 /opt/tomcat`, 
`sudo apt-get install -y mongodb`, 
`sudo apt-get install -y postgresql`, 
and `sudo apt-get install -y redis-server`. 
Configure your project’s `.env` file with 
`POSTGRES_DB=database`, 
`POSTGRES_USER=myuser`, 
`POSTGRES_PASSWORD=password`, 
`MONGO_INITDB_DATABASE=database`, 
`POSTGRES_HOST=localhost`, 
`POSTGRES_PORT=5432`, 
`REDIS_PORT=6379`. 
Set up Tomcat by editing `tomcat-users.xml` with 
`sudo nano /opt/tomcat/conf/tomcat-users.xml` 
and adding 
`<role rolename="manager-gui"/>
<role rolename="admin-gui"/>
<user username="admin" password="your_password" roles="manager-gui,admin-gui"/>`. 
Remove the `ROOT` folder from Tomcat and deploy your WAR file with 
`sudo rm -rf /opt/tomcat/webapps/ROOT`, 
`sudo cp /path/to/your/project.war /opt/tomcat/webapps/ROOT.war`, 
`sudo /opt/tomcat/bin/shutdown.sh`, and `sudo /opt/tomcat/bin/startup.sh`. 
Restart all services with `sudo /opt/tomcat/bin/shutdown.sh`, 
`sudo /opt/tomcat/bin/startup.sh`, 
`sudo systemctl restart mongodb`, 
`sudo systemctl restart postgresql`, 
and `sudo systemctl restart redis-server`. 
Check app on localhost:8080
