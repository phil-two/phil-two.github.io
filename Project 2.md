For those who don’t know markdown, here is a cheat sheet: [https://www.markdownguide.org/cheat-sheet/](https://www.markdownguide.org/cheat-sheet/)

# 

# Project 2 \- Wordpress through Docker Container

## **Prerequisites**

1. Type sudo apt update  
2. Type sudo apt upgrade  
3. Type sudo apt install docker.io  
4. Type sudo apt install docker-compose

## **Create the project directory**

1. Type mkdir wordpress to make a directory named wordpress  
2. Type cd wordpress to change into that directory  
3. Type nano docker-compose.yml  
4. In that file, paste

version: '3'  
services:  
  db:  
    image: mysql:5.7  
    volumes:  
      \- db\_data:/var/lib/mysql  
    restart: always  
    environment:  
      MYSQL\_ROOT\_PASSWORD: your\_mysql\_root\_password  
      MYSQL\_DATABASE: wordpress  
      MYSQL\_USER: wordpress  
      MYSQL\_PASSWORD: your\_mysql\_password  
  wordpress:  
    depends\_on:  
      \- db  
    image: wordpress:latest  
    ports:  
      \- 8000:80  
    restart: always  
    volumes:  
      \- wp\_data:/var/www/html  
    environment:  
      WORDPRESS\_DB\_HOST: db:3306  
      WORDPRESS\_DB\_USER: wordpress  
      WORDPRESS\_DB\_PASSWORD: your\_mysql\_password  
volumes:  
  db\_data: {}  
  wp\_data: {}

## **Starting docker**

1. Type cd to exit the directory and return to the home directory  
2. Type docker-compose up \-d  
3. Access your web server  
   

## **Stopping docker**

4. Type docker-compose down

Resources:   
[How to Install WordPress on Docker in 2024 \[Step-By-Step Guide\]](https://runcloud.io/blog/install-wordpress-on-docker)

Documentation Completed by:   
Philip Tu  
