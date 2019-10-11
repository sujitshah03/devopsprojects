Default java version in AWS Centos

```
java -version

```
java version "1.7.0_201"
OpenJDK Runtime Environment (amzn-2.6.16.0.78.amzn1-x86_64 u201-b00)
OpenJDK 64-Bit Server VM (build 24.201-b00, mixed mode)

```
sudo yum list | grep java-1.8

sudo yum install java-1.8.0-openjdk-devel.x86_64 -y

sudo update-alternatives --config java

```

There are 2 programs which provide 'java'.

  Selection    Command
-----------------------------------------------
*+ 1           /usr/lib/jvm/jre-1.7.0-openjdk.x86_64/bin/java
   2           /usr/lib/jvm/jre-1.8.0-openjdk.x86_64/bin/java


```
Enter to keep the current selection[+], or type selection number: 2

```

```
java -version

```

```
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key

sudo yum install jenkins

sudo service jenkins start

```

Install Apache Maven

```

cd /opt

sudo wget http://www-eu.apache.org/dist/maven/maven-3/3.5.4/binaries/apache-maven-3.5.4-bin.tar.gz

sudo tar xzf apache-maven-3.5.4-bin.tar.gz

sudo ln -s apache-maven-3.5.4 maven

sudo vi /etc/profile.d/maven.sh

export M2_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}

source /etc/profile.d/maven.sh

mvn -version

sudo rm -f /opt/apache-maven-3.5.4-bin.tar.gz

```
install git

```
sudo yum install git -y
```

## Tomcat server Installation in Another App server

install and configure java and java_home
```
sudo yum update
sudo yum list | grep java-1.8
sudo yum install java-1.8.0-openjdk-devel.x86_64 -y
sudo update-alternatives --config java
```
Enter to keep the current selection[+], or type selection number: 2
* update JAVA_HOME
```
nano .bashrc
export JAVA_HOME="/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.201.b09-0.amzn2.x86_64"
export PATH=$JAVA_HOME/bin:$PATH
source .bashrc
echo $JAVA_HOME
```


* Installing Apache Tomcat 9

```
cd /opt

sudo wget http://www-us.apache.org/dist/tomcat/tomcat-9/v9.0.27/bin/apache-tomcat-9.0.27.tar.gz

sudo tar -xvf apache-tomcat-9.0.27.tar.gz

sudo mv apache-tomcat-9.0.27 tomcat9

echo "export CATALINA_HOME="/opt/tomcat9"" >> ~/.bashrc

source ~/.bashrc

```
start tomcat server

```
cd /opt

sudo chown -R ec2-user:ec2-user tomcat9

cd tomcat9/bin

./startup.sh 

```

* visit http://Your-IP-Address:8080


