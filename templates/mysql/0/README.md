# MySQL

## What is MySQL?

Mysql clients are installed on host labeled `mysql=1`
Mysql-lb is installed on host labeled `mysql=1`
phpmyadmin is installed on host labeled `mysql=1`

Once deployed, use a mysql client to connect:

`mysql -u root -p -h<mysql-lb>`

(No user database is installed at startup)

## Services

Includes the following services:
- Load Balancer
- MySQL Server
- MySQL Data (sidekick to the server)
- phpmyadmin

## Usage

The minimum configuration option(s) required to launch the stack is the MySQL Public LB Port and MySQL Root Password. See the description of each option for more information.
