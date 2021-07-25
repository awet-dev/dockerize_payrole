# Pay Role Staff

### Clone the project from GitHub
- Clone the project from [git](https://github.com/awet100/pay-sales-staff)
- It is public, clone and run the command below

### After cloning the project, first thing
- `./start.sh` to start the docker container for this project
- if you want to stop the container run `./stop.sh`

### To run the command below 
- You should go to the php-fpm container to run the commands below
- To do that move to docker and run the command below,
- Run `cd docker` in new terminal to go the directory where the commands exist, which is docker.
- Then run `docker exec -it php-fpm /bin/bash`

### Install all the dependency run
- `composer install` to install php dependency
- `yarn install` to install javascript dependency


### Create database and persist, Run 
- `bin/console d:d:create` to create database, you should run this once for each creation of image
- `bin/console d:s:u --force` to persist the entity to the database

### To start the serve, Run
- `symfony server:ca:install` if you want to run the web server with TLS support, and then 
- `symfony serve -d` to start the server and run symfony app in docker container
- `yarn watch` to build the javascript asset for the project


### What to do with the app
- After the app start, go to http://127.0.0.1:5000
- Then login, and creat customer that you are going to make transaction to as a supplier.
- Add the product you have in the company, add all the required detail about the product by clicking http://127.0.0.1:5000/admin
- Then you can make transaction of the provided product to the customer by clicking to the transaction button and then addTransaction 

### Salary and bonus
- The salary is paid at the last working day of the month.
- If the last day is holiday, it will be executed in the last working day.
- It is handled by javascript 
- And the bonus of this month is going to be paid in the mid of the next month 
- Meaning at 15th of the next month, if it is holiday, it will be postponed to the next wednesday after 15th of the next month
- This is totally automated and handled by javascript.