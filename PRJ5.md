# Client Server Architecture using MySQL DBMS - Project 5

The first step is to login to AWS EC2. Why inside AWS EC2, we created two Instances. One is named MySQL-Server and the other MySSQL-Client.

`git init`
This command will take us to Github repository.

`sudo apt update`
Once inside github repository, I update my terminal with the above command.

![Terminal updated](./Terminal update.png)

`sudo apt upgrade`
Upgrade the terminal with this command.

`sudo apt install mysql-server -y`
This command is used to install mysql server.

![Installation of mysql server](./MySql Server installed.png)

`sudo systemctl status mysql` 
This command was used to confirm the status of our just installed server.

![Confirmation of installed mysql server](./mysql server confirmation.png)

`sudo systemctl enable mysql`
This command was used to enable mysql server.

At this point, we updated our EC2 Instance security group by adding MYSQL/Aurora to the inbound rules.

![Security Group update](./Add rules to EC2 Instance Security Group.png)

At this point move from mysql-server and let us open a second terminal. We're going to get mysql-client installed on this second terminal. We're going to copy our ssh example code from mysql-client EC2 Instance.

`cd downloads`
Use the cd downloads command while inside this terminal.
Then paste mysql-client EC2 Instance ssh example code. And then press enter.

`mkdir PRJ5`
We created PRJ5 directory for mysql-client

`cd PRJ5`
We used this command to change into this directory.

![ClientServer directory created](./PRJ5.md created.png)

`sudo apt install mysql-client`
This command was used to install mysql-client.

At this point, we're going to copy mysql-client AWS EC2 Instance Private IP address and place it in Mysql-server security group inbound rules CIDR Blocks. We are doing this because we have to secure the server so that other IP addresses cannot just connect to this server.

Go back to mysql-server terminal and do the following:

`sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf`
This is use to reconfigure mysql server to allow connections from remote hosts.

![Reconfigure mysql server](./Reconfigure mysql server.png)

`sudo mysql`
Used this command to enter mysql

![User,host table](./USER HOST.png)

`CREATE USER 'client'@'%' IDENTIFIED BY 'PassWord.1';`

`GRANT ALL PRIVILEGES ON *.* TO 'client'@'%' WITH GRANT OPTION;`

`FLUSH PRIVILEGES`

`select user,host from mysql.user;`

`show databases;`

![show databases](./show databases.png)

`mysql -h 172.31.89.19 -u client -p`
Enter the command in mysql-server. Then enter your password.

`sudo systemctl restart mysql`
In mysql-server, restart the server with this command.

`mysql -h 172.31.89.19 -u client -p`
Then go your mysql-client, and enter the command above. Then enter your password.

`select user,host from mysql.user;`

![user,host from mysqi.user](./client user.png)

`show databses` for client.

![show databases](./show databasesClient.png)

