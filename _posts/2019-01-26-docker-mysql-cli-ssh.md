---
layout: post
title: "Connect to a remote Docker container with the MySQL CLI over SSH"
date: 2019-01-26
tags: mysql docker ssh
---

# But why though?? :raising_hand:
The website I'm currently working on is made up of 5 networked Docker containers, 1 of which (the database) is running a MySQL instance. We also use 3 different hosts (`dev`, `test`, and `prod`), all of which are running their own instances of these containers.

Anywaaay, by putting the function below in your `.bashrc` you can simply run `sql [server1, server2, server3]` and the function will:
* SSH to the specified host
* Source a file containing that host's MySQL credentials and store the password in a `$DB_MYSQL_PASSWORD`
* Inspect the running database container, and pipe that into `jq`, which is used to grab that container's local IP address, which is then stored in `$ip`
* Using that information, connect to the running Docker container using the MySQL CLI

# sql() :ok_hand:
*Note: Server needs to have `jq` installed.*

```shell
sql() {
        case $1 in
                "server1") ssh -t user@server1.com 'source /path/to/mysql/credentials.env; ip=$(sudo docker inspect mysql_docker_img | jq --raw-output .[].NetworkSettings.Networks.docker_network_name.IPAddress); mysql -h $ip -P3306 -u root -p$DB_MYSQL_PASSWORD';;
                "server2") ssh -t user@server2.com 'source /path/to/mysql/credentials.env; ip=$(sudo docker inspect mysql_docker_img | jq --raw-output .[].NetworkSettings.Networks.docker_network_name.IPAddress); mysql -h $ip -P3306 -u root -p$DB_MYSQL_PASSWORD';;
                "server3") ssh -t user@server3.com 'source /path/to/mysql/credentials.env; ip=$(sudo docker inspect mysql_docker_img | jq --raw-output .[].NetworkSettings.Networks.docker_network_name.IPAddress); mysql -h $ip -P3306 -u root -p$DB_MYSQL_PASSWORD';;
        esac
}
```
