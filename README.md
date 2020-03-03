```bash
npm install
```

create db
```bash
mysql -u root -p
# enter pass for local computer. This is not the docker section yet

# crate todo db
create database ctodo;

 # then create table
 CREATE TABLE IF NOT EXISTS `customers` (
 id int(11) NOT NULL PRIMARY KEY AUTO_INCREMENT,
 email varchar(255) NOT NULL,
 name varchar(255) NOT NULL,
 active BOOLEAN DEFAULT false
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


### OPTIONAL
# create user. restrict to this machine localhost !! OPTIONAL - could use root
create user 'utodo'@'localhost' identified by 'utodo';

# grant user priv for db !! OPTIONAL - could use root
GRANT ALL PRIVILEGES ON ctodo.* to 'utodo'@'localhost';

 ```

 Create the docker image of the application
 ***-t*** adds tag to build
 ```bash
 docker build -t node-prod .
 ```

 Once built we can run the server
 ```bash
 docker run -d -p 8000:8000 node-prod // run detached
 docker run -it -p 8000:8000 node-prod // run interactive
 ```

 Live reloading option for development
 ```bash
 docker build -f Dockerfile.dev -t node-dev .
 docker run --rm -it -p 8000:8000 -v ${PWD}:/app node-dev
 ```