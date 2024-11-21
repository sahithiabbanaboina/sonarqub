# sonarqub
code for installing sonar
sudo apt update
sudo apt install openjdk-11-jdk -y
sudo apt install postgresql postgresql-contrib -y
sudo systemctl start postgresql
sudo systemctl enable postgresql

#edit
CREATE USER sonaruser WITH PASSWORD 'yourpassword';
CREATE DATABASE sonardb;
GRANT ALL PRIVILEGES ON DATABASE sonardb TO sonaruser;
\q

wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.9.0.65466.zip
sudo apt install unzip -y
unzip sonarqube-9.9.0.65466.zip
sudo mv sonarqube-9.9.0.65466 /opt/sonarqube
sudo chown -R ubuntu:ubuntu /opt/sonarqube

sudo apt install postgresql postgresql-contrib -y
sudo systemctl start postgresql
sudo systemctl enable postgresql
sudo -u postgres psql

#edit 
CREATE USER sonaruser WITH PASSWORD 'yourpassword';
CREATE DATABASE sonardb;
GRANT ALL PRIVILEGES ON DATABASE sonardb TO sonaruser;
\q

wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.9.0.65466.zip
sudo apt install unzip -y

unzip sonarqube-9.9.0.65466.zip
sudo mv sonarqube-9.9.0.65466 /opt/sonarqube
sudo chown -R ubuntu:ubuntu /opt/sonarqube

sudo nano /opt/sonarqube/conf/sonar.properties
sonar.jdbc.url=jdbc:postgresql://localhost:5432/sonardb
sonar.jdbc.username=sonaruser
sonar.jdbc.password=yourpassword

