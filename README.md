# docker-letsencrypt-nginx-proxy-wordpress

#Step 1 - Bdd
création de la base et du user dans mariadb
infortion user & password à reporter sur le .env

#exemple 
--DROP DATABASE IF EXISTS MyBdd;
CREATE DATABASE MyBdd;
CREATE USER MyUser IDENTIFIED BY 'MyPassword';
GRANT ALL PRIVILEGES ON MyBdd.* TO MyUser;
FLUSH PRIVILEGES;
SHOW GRANTS FOR MyUser;


#Step 2 - Droits
Après démarage du container changer les droits des dosseirs de l'hôte
#Pour les plugins 
chmod 777 -R /var/docker/wpress

#voir la date de fin du certificat
openssl x509 -in monDomaine.crt -enddate


