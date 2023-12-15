To-DO app  with MySQL Docker and k8 Setup
FRONTEND:
![image](https://github.com/Dilipkumar-M/two-tier-app/assets/84618503/65ea824b-356b-4e7e-9307-dfd3efcffcd9)

![image](https://github.com/Dilipkumar-M/two-tier-app/assets/84618503/c35024fa-e436-40bd-aa40-c980d7565f28)
 Above Screen is the O/P got from the Docker with a port ip:5000
 
![k8s](https://github.com/Dilipkumar-M/two-tier-app/assets/84618503/59376c75-ec7b-414f-a312-49fcd5f8f2e5)
 Above Screen is the O/P got from the k8s with a node ip:30004

![image](https://github.com/Dilipkumar-M/two-tier-app/assets/84618503/c1ee3823-ee4d-4ba0-a428-a19b1d0eae93)

 At the Backend the message will be stored in the backend of mysql server.

 ubuntu@ip-172-31-24-82:~/two-tier-app$ docker ps
CONTAINER ID   IMAGE             COMMAND                  CREATED              STATUS              PORTS                                                  NAMES
d4834a6edbe2   mysql:5.7         "docker-entrypoint.s…"   About a minute ago   Up About a minute   0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql
e8c94d18ef9c   flaskapp:latest   "python app.py"          4 minutes ago        Up 4 minutes        0.0.0.0:5000->5000/tcp, :::5000->5000/tcp              flaskapp
ubuntu@ip-172-31-24-82:~/two-tier-app$ docker exec -it d4834a6edbe2 bash
bash-4.2# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 3
Server version: 5.7.44 MySQL Community Server (GPL)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| myDb               |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)

mysql> use myDb;
Database changed
mysql> CREATE TABLE messages (
    ->     id INT AUTO_INCREMENT PRIMARY KEY,
    ->     message TEXT
    -> );
Query OK, 0 rows affected (0.01 sec)

mysql> show tables;
+----------------+
| Tables_in_myDb |
+----------------+
| messages       |
+----------------+
1 row in set (0.00 sec)

mysql> select * from messages;
+----+------------------------------------------------------------------------------------------------------------------------------------------+
| id | message                                                                                                                                  |
+----+------------------------------------------------------------------------------------------------------------------------------------------+
|  1 | To-Do list app developed by DilipKumar using Docker and k8s, find the Database in Backend entering the text messages or your to-do list. |
+----+------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

![image](https://github.com/Dilipkumar-M/two-tier-app/assets/84618503/9e030748-3e2b-447b-93d1-71d469dd147f)

Output shown in the above image is the database stored in backend entered by a user.

 


