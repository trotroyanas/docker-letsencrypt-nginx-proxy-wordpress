# docker-letsencrypt-nginx-proxy-wordpress

#Step 1_
copy .env.sample .env_
modification des éléments dans .env_


#Step 2
./start.sh pour la toute premiere fois 

docker-compose up -d pour les autres fois
docker-compose down pour killer tous les dockers du docker-compose

#Step 3
création de la base et du user dans mariadb (les memes que ceux du .env)
information : user & password à reporter sur le .env

#exemple 
--DROP DATABASE IF EXISTS MyBdd;
CREATE DATABASE MyBdd;
CREATE USER MyUser IDENTIFIED BY 'MyPassword';
GRANT ALL PRIVILEGES ON MyBdd.* TO MyUser;
FLUSH PRIVILEGES;
SHOW GRANTS FOR MyUser;


#Step 4 - Droits
Après démarage du container changer les droits des dossiers de l'hôte
#Pour les plugins 
chmod 777 -R /var/docker/wpress (affiner les droits, c'est pour les plugins et autres uploads)

#Step 5 - Upload (changer si necessaire)
le repertoire ./php/php.ini
contient par defaut :
  file_uploads = On
  memory_limit = 64M
  upload_max_filesize = 64M
  post_max_size = 64M
  max_execution_time = 600

set client body size to XXXM #
client_max_body_size XXXM;
detruire et refaire le docker wpress pour activer les cgangements 


#voir la date de fin du certificat
openssl x509 -in monDomaine.crt -enddate


