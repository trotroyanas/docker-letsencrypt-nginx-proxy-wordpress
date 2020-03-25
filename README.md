# docker-letsencrypt-nginx-proxy-wordpress

#Step 1 <br>
copy .env.sample .env <br>
modification des éléments dans .env <br>


#Step 2 <br>
./start.sh pour la toute premiere fois <br>
<br>
docker-compose up -d pour les autres fois<br>
docker-compose down pour killer tous les dockers du docker-compose<br>
<br>
#Step 3<br>
création de la base et du user dans mariadb (les memes que ceux du .env)<br>
information : user & password à reporter sur le .env<br>
<br>
#exemple <br>
--DROP DATABASE IF EXISTS MyBdd;<br>
CREATE DATABASE MyBdd;<br>
CREATE USER MyUser IDENTIFIED BY 'MyPassword';<br>
GRANT ALL PRIVILEGES ON MyBdd.* TO MyUser;<br>
FLUSH PRIVILEGES;<br>
SHOW GRANTS FOR MyUser;<br>
<br>
#Step 4 - Droits<br>
Après démarage du container changer les droits des dossiers de l'hôte<br>
#Pour les plugins <br>
chmod 777 -R /var/docker/wpress (affiner les droits, c'est pour les plugins et autres uploads)<br>
<br>
#Step 5 - Upload (changer si necessaire)<br>
le repertoire ./php/php.ini<br>
contient par defaut :<br>
  file_uploads = On<br>
  memory_limit = 64M<br>
  upload_max_filesize = 64M
  post_max_size = 64M<br>
  max_execution_time = 600<br>
<br>
set client body size to XXXM #<br>
client_max_body_size XXXM;<br>
detruire et refaire le docker wpress pour activer les changements <br>
<br>
<br>
#voir la date de fin du certificat<br>
openssl x509 -in monDomaine.crt -enddate<br>


