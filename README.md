# Pay Role Staff

### Clone the project from GitHub
- Clone the project from [git](https://github.com/awet100/dockerize_payrole)
- It is public, clone and run the command below

### After cloning the project, first thing
- `./start.sh` to start the docker container for this project
- if you want to stop the container run `./stop.sh`

### To run the command below 
- You should go to the php-fpm container to run the commands below
- To do that move to docker and run the command below,
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
- `yarn build` to build the javascript asset for the project


### What to do with the app
- Open `pay-sales-staff/src/Entity/User.php` and add `$this->setRoles(['ROLE_ADMIN']);` inorder to create a user with `Role_ADMIN`
- Then create an account on http://127.0.0.1:5000 (i.e. registration page). The password has to be min 6 characters
- Then it will direct you to the login page, login and have access to the back end.
- Remove the `$this->setRoles(['ROLE_ADMIN']);` from the `pay-sales-staff/src/Entity/User.php`

### What can user with ROLE_ADMIN can do?
- Create Supplier and another Admin from the already created user just by changing the `ROLE_USER` to `ROLE_SUPPLIER` and `ROLE_ADMIN`
- Can do what the supplier can do, after adding the `ROLE_SUPPLIER` 

### What can Supplier do?
- Create Customer and Product that is available for sales in the company.
- Make transaction for the Customer for the selected Product. 

### Salary and bonus
- As the result of the transaction done, Bonus will be added to te supplier
- And the bonus of this month is going to be paid in the mid of the next month
- Meaning at 15th of the next month, if it is holiday, it will be postponed to the next wednesday after 15th of the next month
- The salary is paid at the last working day of the month.
- If the last day is holiday, it will be executed in the last working day
- This is totally automated and handled by javascript.

### CSV file report
- to get the csv report for the salary and bonus download it from the admin dashboard