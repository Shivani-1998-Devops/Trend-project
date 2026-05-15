# Ttrend application

This is a small applicaiton which contains main and test folders.  
Main contains application code.  
Test contains test cases.  
It also contains pom.xml which has all dependences and artfact name and version

###-----------maven steps---------

Run this command:
```bash
sudo wget https://archive.apache.org/dist/maven/maven-3/3.9.2/binaries/apache-maven-3.9.2-bin.tar.gz

After download completes:

Extract Maven
sudo tar -xvzf apache-maven-3.9.2-bin.tar.gz
Verify Extraction
ls /opt

You should see:

apache-maven-3.9.2
apache-maven-3.9.2-bin.tar.gz
Configure Maven

Create file:

sudo vi /etc/profile.d/maven.sh

Add:

export M2_HOME=/opt/apache-maven-3.9.2
export PATH=${M2_HOME}/bin:${PATH}
Apply Configuration
source /etc/profile.d/maven.sh
Verify Maven
mvn -version

Expected:

Apache Maven 3.9.2
Java version: 11
```
