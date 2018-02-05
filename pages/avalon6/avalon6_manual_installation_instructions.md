---
title: Manual Installation Instructions
summary: "Instructions for installing an all-in-one Avalon Media System from scratch."
sidebar: avalon6_sidebar
permalink: avalon6_manual_installation_instructions.html
folder: avalon6
---

These instructions provide a recipe for building your own all-in-one Avalon system from scratch on CentOS or Red Hat Enterprise Linux; version 6.x is currently supported, 7.x will be supported soon. Please note that while an all-in-one installation as outlined here is certainly suitable for testing and demos, a single all-in-one server may not be suitable for production environments.

## Ready the Installation Environment

__Make sure a valid hostname is resolvable__

The default hostname is `avalon.dev`, so name the machine this and enter it into `/etc/hosts`

    # hostname
    avalon.dev
    # cat /etc/hosts
    127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4 avalon.dev

__Configure iptables__

The Avalon Media System requires several ports to be open to client browsers. Here are the port settings that will need to be configured:

|------|-------------------|-----------|
| Port | Purpose           | External? |
|------|-------------------|-----------|
| 80   | HTTP (Avalon)     | Yes       |
| 8983 | HTTP (Solr)       | No        |
| 8984 | HTTP (Fedora)     | No        |
| 8080 | HTTP (Matterhorn) | Yes       |
|------|-------------------|-----------|

The preferred method is to create a shell script that will do the work for you. Here is an example script that you should look through and customize as needed: [avalon-iptables-config.sh](https://wiki.dlib.indiana.edu/download/attachments/515276965/avalon-iptables-config.sh?version=1&modificationDate=1381259701000&api=v2)

{{ site.data.alerts.warning }}
If you are connected over ssh, you might be kicked off.
{{ site.data.alerts.end }}

Save your script to `/etc/sysconfig/avalon-iptables-config.sh`, make it executable and run it.

    chmod +x /etc/sysconfig/avalon-iptables-config.sh
    /etc/sysconfig/avalon-iptables-config.sh

If you run into connection issues you can disable the iptables, by running `service iptables stop`. This will completely drop your firewall. When finished troubleshooting run `service iptables start`.

__Disable SELinux__

    echo 0 > /selinux/enforce
    vim /etc/selinux/config #change the value of `SELINUX` from `enforcing` to `permissive`

{{site.data.alerts.note}}
You may have to disable SELinux completely if there is a Passenger installation problem.
<pre>
vim /etc/selinux/config #change the value of `SELINUX` to `disabled`
</pre>
{{site.data.alerts.end}}

__Install EPEL__

This package has libyaml-devel which is required by ruby and not provided by Redhat.

    rpm -ivh http://linux.mirrors.es.net/fedora-epel/6/i386/epel-release-6-8.noarch.rpm

__Add the Avalon repository__

Create the Avalon repository config file:

    vim /etc/yum.repos.d/avalon-public.repo

Append the following code:

    [avalon_public]
    name=Avalon Public RHEL repository
    baseurl=http://repo.avalonmediasystem.org/x86_64
    enabled=1
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-avalon
    cost=150
    
Install and place the Avalon GPG key in the proper location:

    curl http://repo.avalonmediasystem.org/RPM-GPG-KEY-avalon -o /etc/pki/rpm-gpg/RPM-GPG-KEY-avalon

Install development libraries and packages for building Ruby

    yum groupinstall "Development Tools"
    yum install readline-devel zlib-devel libyaml-devel libffi-devel openssl-devel libxml2-devel libxslt-devel cmake

__Install Java 8__

    yum install java-1.8.0-openjdk


## Main Components

### Fedora Commons Repository

Fedora runs as a webapp in Tomcat

__Install Apache Tomcat__

    yum install tomcat
    vim /etc/tomcat/server.xml #line 71, change the Tomcat connector port from 8080 to 8984

__Add Tomcat manager user__

By default, no user has access to the Tomcat Manager App. Define a user in `/etc/tomcat/tomcat-users.xml` with access to the manager-gui role. Below is a very basic example.

    <tomcat-users>
      <role rolename="manager-gui"/>
      <user username="admin" password="<insert strong password here>" roles="manager-gui"/>
    </tomcat-users>

__Configure Tomcat for Fedora__

Append the following to `/etc/sysconfig/tomcat`

    JAVA_OPTS="${JAVA_OPTS} -Dfcrepo.modeshape.configuration=classpath:/config/file-simple/repository.json -Dfcrepo.home=/var/avalon/fedora/"

__Restart Tomcat__

    service tomcat restart

Download and run the fcrepo installer

    mkdir -p /var/avalon/fedora
    chown tomcat:tomcat /var/avalon/fedora
    wget https://github.com/fcrepo4/fcrepo4/releases/download/fcrepo-4.7.3/fcrepo-webapp-4.7.3.war -O /usr/share/tomcat/webapps/fedora4.war

See if you can access Fedora's REST interface at `http://<server host name>:8984/fedora4/rest`

Try it out on your local machine and on another machine. If you can't reach the app from another machine, your iptables might need to be changed to allow access. If Fedora is not up, check the tomcat logs in `/var/log/tomcat/`. `Catalina.out` and `localhost.<date>.log` usually provide the best information.

### Solr

Avalon makes use of Solr through the Blacklight gem for faceting and relevance-based searching.

__Install prerequisites__

    yum install lsof

__Download Solr tarball and run the installation script__

Download Solr from [http://archive.apache.org/dist/lucene/solr/](http://archive.apache.org/dist/lucene/solr/)

    wget http://archive.apache.org/dist/lucene/solr/6.4.2/solr-6.4.2.tgz
    tar xzf solr-6.4.2.tgz solr-6.4.2/bin/install_solr_service.sh --strip-components=2
    bash ./install_solr_service.sh solr-6.4.2.tgz

By default, the script extracts the distribution archive into `/opt`, configures Solr to write files into `/var/solr`, and runs Solr as the solr user. Follow the linked guide if you wish to change these defaults.

__Create Avalon core for Solr__

    mkdir -p /tmp/avalon_solr/
    wget https://raw.githubusercontent.com/avalonmediasystem/avalon/master/solr/config/solrconfig.xml -O /tmp/avalon_solr/solrconfig.xml
    wget https://raw.githubusercontent.com/avalonmediasystem/avalon/master/solr/config/schema.xml -O /tmp/avalon_solr/schema.xml
    su solr # Needs to run as solr user
    /opt/solr/bin/solr create_core -c avalon -d /tmp/avalon_solr
    exit

If you have successfully installed Solr you should be able to access the dashboard page at `http://<server host name>:8983/solr`

Instructions on how to manually start/stop Solr: [https://cwiki.apache.org/confluence/display/solr/Running+Solr](https://cwiki.apache.org/confluence/display/solr/Running+Solr)

### MySQL

{% include note.html content="MariaDB is now the default database system for CentOS/RHEL7. Feel free to change MySQL below to MariaDB." %}

Avalon uses MySQL for storing search queries, user data and roles, and as a back end for asynchronously sending requests to Matterhorn. 

__Install MySQL server__

    yum install mysql-server
    service mysqld start

__Create databases and users__

Enter the mysql monitor

    #mysql
    Welcome to the MySQL monitor. Commands end with ; or \g.
    ...etc...
    mysql>

Create a database for the Avalon web application and add a user to it

    create database rails;
    create user 'rails'@'localhost' identified by 'rails';
    grant all privileges on rails.* to 'rails'@'localhost';
    flush privileges;

Check your work and exit
    
    mysql> show databases;
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | rails              |
    | test               |
    +--------------------+
    5 rows in set (0.00 sec)
    mysql> select user, host from mysql.user;
    +--------+--------------+
    | user   | host         |
    +--------+--------------+
    | root   | 127.0.0.1    |
    |        | 129.79.32.87 |
    | root   | 129.79.32.87 |
    |        | localhost    |
    | rails  | localhost    |
    | root   | localhost    |
    +--------+--------------+
    7 rows in set (0.00 sec)
      
    mysql> exit;
    Bye

See documentation for your version of MySQL Server for detailed syntax: [http://dev.mysql.com/doc/refman/5.1/en/create-database.html](http://dev.mysql.com/doc/refman/5.1/en/create-database.html)

{% include links.html %}