docker-compose.yaml
version: '3'
service: 
        wordpress:
          depends_on:
             - mysql
          image: wordpress:4.9.4-php7-apache
          container_name: ws
          environment: 
             - WORDPRESS_DB_USER=root
             - WORDPRESS_DB_PASSWORD=school1
             - WORDPRESS_DB_HOST=mysql
             - WORDPRESS_DB_NAME=webserver
          ports:
             - 3010:80
          networks:
             - web
          volume:
             - wordpress:/var/www/html

        mysql:
            image: mariadb:10.3.3
            container_name: db
            environment:
             - MYSQL_ROOT_PASSWORD=school1
             - MYSQL_USER=oracle
             - MYSQL_PASSWORD=school1
             - MYSQL_DATABASE=webserver
            network:
             - web
            volumes:
             -database:/var/lip/mysql

networks:
   web:
      driver: bridge
volumes:
   wordpress:
   database:



          

