# docker-letsencrypt-nginx-proxy-wordpress

#Step 1 - Bdd
création de la base et du user dans mariadb.
information : user & password à reporter sur le .env

#exemple 
--DROP DATABASE IF EXISTS MyBdd;
CREATE DATABASE MyBdd;
CREATE USER MyUser IDENTIFIED BY 'MyPassword';
GRANT ALL PRIVILEGES ON MyBdd.* TO MyUser;
FLUSH PRIVILEGES;
SHOW GRANTS FOR MyUser;


#Step 2 - Droits
Après démarage du container changer les droits des dossiers de l'hôte
#Pour les plugins 
chmod 777 -R /var/docker/wpress

#Step 3 - Upload
modifier la conf de Nginx pour permettre un upload plus important.
Du container nginx-web
# vi /etc/nginx/nginx.conf
OR
# vi /usr/local/nginx/conf/nginx.conf
Add the following line to http or server or location context to increase the size limit in nginx.conf, enter:
# set client body size to 256M #
client_max_body_size 256M;

Save and close the file. Reload the nginx webserver, enter:
# /usr/local/nginx/sbin/nginx -s reload
Or
# restart le container

#voir la date de fin du certificat
openssl x509 -in monDomaine.crt -enddate


