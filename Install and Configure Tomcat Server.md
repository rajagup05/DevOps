
## Day 11: Install and Configure Tomcat Server

`Task`: The application development team recently finished the beta version of one of their Java-based applications, which they are planning to deploy on one of the app servers in Stratos DC. After an internal team meeting, they have decided to use the tomcat application server. Based on the requirements mentioned below complete the task:

a. Install `tomcat` server on `App Server 1`.
b. Configure it to run on port `3001`.
c. There is a `ROOT.war` file on Jump host at location `/tmp`.

Deploy it on this `tomcat` server and make sure the webpage works directly on base URL i.e `curl http://stapp01:3001` 

### solution: 

**1. Install Tomcat**
- used $ `sudo yum install tomcat -y` to install tomcat 
- used $ `ls -l /etc/tomcat/` to see the files under tomcat folder:
```
total 240
drwxrwxr-x 3 root tomcat   4096 Apr 17 06:39 Catalina
-rw-r--r-- 1 root tomcat  13347 Mar 13 14:35 catalina.policy
-rw-r--r-- 1 root tomcat   7654 Mar 13 14:35 catalina.properties
drwxr-xr-x 2 root tomcat   4096 Apr 17 06:39 conf.d
-rw-r--r-- 1 root tomcat   1400 Mar 13 14:35 context.xml
-rw-rw-r-- 1 root tomcat   1149 Mar 13 14:35 jaspic-providers.xml
-rw-rw-r-- 1 root tomcat   2313 Mar 13 14:35 jaspic-providers.xsd
-rw-r--r-- 1 root tomcat   4003 Mar 13 14:35 logging.properties
-rw-r--r-- 1 root tomcat   8022 Mar 13 14:35 server.xml
-rw-r----- 1 root tomcat   3231 Mar 13 14:35 tomcat-users.xml
-rw-rw-r-- 1 root tomcat   2558 Mar 13 14:35 tomcat-users.xsd
-rw-r--r-- 1 root tomcat   1828 Mar 13 14:35 tomcat.conf
-rw-r--r-- 1 root tomcat 173782 Mar 13 14:35 web.xml
```

### 2. Configure Port 3001

- used $ `sudo vi /etc/tomcat/server.xml` to find the `<Connector>` tag that specifies `port="8080"` and changed it to port="3001". Saved and exited.

### 3. Deploy the ROOT.war 

- To make the application accessible at the base URL (e.g., `http://stapp01:3001`), you must replace the default Tomcat root directory:  Clear the existing webapps content:
```
$ sudo rm -rf /var/lib/tomcat/webapps/ROOT*
```
- Copy the `ROOT.war` from the `Jump host` to `App Server 1`. From the Jump host:
```
thor@jump-host ~$ scp /tmp/ROOT.war tony@stapp01:/tmp
tony@stapp01's password: 
ROOT.war                   
```

- Move the file to the Tomcat deployment directory on App Server 1:
```
$ sudo mv /tmp/ROOT.war /var/lib/tomcat/webapps/
```

### 4. Start the Service

- Start and enable Tomcat to ensure the changes take effect:
```
$ sudo systemctl enable tomcat
sudo systemctl start tomcat 
```

### 5. Verify

- Run the curl command to check if the deployment was successful: 
$ `curl http://stapp01:3001`
```
<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html>
    <head>
        <title>SampleWebApp</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <h2>Welcome to xFusionCorp Industries!</h2>
        <br>
    
    </body>
</html>
```

