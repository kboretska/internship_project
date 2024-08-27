# Runbook for Deploying 'Class Schedule' on Debian

## 1. Update Debian

Update your system with the following commands:

```bash
sudo apt-get update && sudo apt-get upgrade -y

## 2. Install Required Components
# Download and install Tomcat 9.0.50
wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.50/bin/apache-tomcat-9.0.50.tar.gz
sudo tar xvf apache-tomcat-9.0.50.tar.gz -C /opt/
sudo mv /opt/apache-tomcat-9.0.50 /opt/tomcat

# Install MongoDB, PostgreSQL, and Redis
sudo apt-get install -y mongodb
sudo apt-get install -y postgresql
sudo apt-get install -y redis-server

## 3. Configure Environment Variables
Update the .env file in your project with the following content:
```bash
POSTGRES_DB=database
POSTGRES_USER=myuser
POSTGRES_PASSWORD=password
MONGO_INITDB_DATABASE=database
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
REDIS_PORT=6379
